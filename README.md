# DNS Performance Test

Shell script to test the performance of the most popular DNS resolvers from your location.

Includes by default:
 * CloudFlare 1.1.1.1
 * Level3 4.2.2.1
 * Google 8.8.8.8
 * Quad9 9.9.9.9
 * Freenom 80.80.80.80
 * OpenDNS
 * Norton
 * CleanBrowsing
 * Yandex
 * AdGuard
 * Neustar
 * Comodo

# Required 

You need to install bc and dig. For Ubuntu:

```
 $ sudo apt-get install bc dnsutils
```

# Utilization

``` 
 $ git clone --depth=1 https://github.com/cleanbrowsing/dnsperftest/
 $ cd dnsperftest
 $ bash ./dnstest.sh 
DNS IP              Provider            test1   test2   test3   test4   test5   test6   test7   test8   test9   test10  Average
127.0.0.1           127.0.0.1           34 ms   20 ms   20 ms   30 ms   19 ms   108 ms  25 ms   18 ms   20 ms   18 ms     31.20
1.1.1.1             cloudflare          49 ms   38 ms   38 ms   38 ms   40 ms   38 ms   39 ms   38 ms   39 ms   39 ms     39.60
4.2.2.1             level3              38 ms   37 ms   38 ms   39 ms   39 ms   39 ms   38 ms   38 ms   39 ms   39 ms     38.40
8.8.8.8             google              39 ms   39 ms   38 ms   45 ms   40 ms   44 ms   40 ms   40 ms   40 ms   39 ms     40.40
9.9.9.9             quad9               39 ms   38 ms   59 ms   227 ms  43 ms   80 ms   42 ms   38 ms   350 ms  42 ms     95.80
80.80.80.80         freenom             157 ms  155 ms  158 ms  156 ms  207 ms  163 ms  155 ms  200 ms  162 ms  212 ms    172.50
208.67.222.123      opendns             43 ms   39 ms   39 ms   38 ms   38 ms   104 ms  43 ms   38 ms   38 ms   38 ms     45.80
199.85.126.20       norton              39 ms   39 ms   38 ms   38 ms   38 ms   38 ms   38 ms   38 ms   38 ms   39 ms     38.30
185.228.168.168     cleanbrowsing       38 ms   53 ms   39 ms   38 ms   40 ms   39 ms   39 ms   38 ms   38 ms   39 ms     40.10
77.88.8.7           yandex              48 ms   55 ms   57 ms   58 ms   54 ms   54 ms   55 ms   56 ms   54 ms   71 ms     56.20
176.103.130.132     adguard             101 ms  103 ms  108 ms  119 ms  132 ms  109 ms  163 ms  129 ms  112 ms  105 ms    118.10
156.154.70.3        neustar             44 ms   38 ms   40 ms   39 ms   37 ms   38 ms   38 ms   38 ms   37 ms   38 ms     38.70
8.26.56.26          comodo              38 ms   38 ms   39 ms   39 ms   38 ms   38 ms   38 ms   38 ms   37 ms   38 ms     38.10
```

To sort with the fastest first, add `sort -k 23 -n` at the end of the command:

```
  $ bash ./dnstest.sh |sort -k 23 -n
DNS IP              Provider            test1   test2   test3   test4   test5   test6   test7   test8   test9   test10  Average
127.0.0.1           127.0.0.1           24 ms   26 ms   18 ms   30 ms   24 ms   114 ms  19 ms   19 ms   21 ms   21 ms     31.60
8.8.8.8             google              37 ms   37 ms   37 ms   37 ms   37 ms   36 ms   37 ms   37 ms   38 ms   37 ms     37.00
156.154.70.3        neustar             37 ms   37 ms   37 ms   37 ms   38 ms   37 ms   37 ms   37 ms   37 ms   37 ms     37.10
8.26.56.26          comodo              36 ms   37 ms   39 ms   37 ms   37 ms   38 ms   37 ms   37 ms   37 ms   37 ms     37.20
4.2.2.1             level3              37 ms   37 ms   38 ms   38 ms   37 ms   37 ms   41 ms   36 ms   37 ms   37 ms     37.50
208.67.222.123      opendns             41 ms   37 ms   37 ms   37 ms   37 ms   37 ms   38 ms   37 ms   40 ms   37 ms     37.80
1.1.1.1             cloudflare          53 ms   37 ms   38 ms   37 ms   37 ms   37 ms   37 ms   37 ms   37 ms   37 ms     38.70
185.228.168.168     cleanbrowsing       42 ms   39 ms   37 ms   37 ms   37 ms   37 ms   37 ms   37 ms   37 ms   56 ms     39.60
77.88.8.7           yandex              55 ms   52 ms   53 ms   56 ms   60 ms   54 ms   52 ms   92 ms   53 ms   85 ms     61.20
199.85.126.20       norton              38 ms   37 ms   37 ms   37 ms   37 ms   37 ms   41 ms   37 ms   37 ms   500 ms    83.80
9.9.9.9             quad9               37 ms   133 ms  500 ms  43 ms   37 ms   37 ms   37 ms   98 ms   59 ms   38 ms     101.90
176.103.130.132     adguard             114 ms  104 ms  111 ms  106 ms  102 ms  108 ms  103 ms  105 ms  103 ms  114 ms    107.00
80.80.80.80         freenom             160 ms  167 ms  184 ms  161 ms  194 ms  251 ms  188 ms  319 ms  167 ms  220 ms    201.10
```

# For Windows users using the Linux subsystem

If you receive an error `$'\r': command not found`, convert the file to a Linux-compatible line endings using:

    tr -d '\15\32' < dnstest.sh > dnstest-2.sh
    
Then run `bash ./dnstest-2.sh`
