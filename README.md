# Go lpm package 

Tree-bitmap least prefix match (LPM) implementation in Go. The information about this algorithm can be found [here](https://cseweb.ucsd.edu/~varghese/PAPERS/willpaper.pdf) It supports both Ipv4/Ipv6 lookups and user-defined data types to be associated with prefixes

# How to use in your project 

Kindly check trie_test.go in this repository which has all the necessary examples 

To add a route -

```
route = "10.10.10.10/32"
// Data can be any user-defined type 
data = 12
res = trieR.AddTrie(route, data)
if res != 0 {
  fmt.Printf("Trie add failed\n")
}
```

To delete a route -

```
route = "10.10.10.10/32"
res = trieR.DelTrie(route)
if res != 0 {
  fmt.Printf("Trie delete failed\n")
}
```

To find a route -

```
ret, ipn, rdata := trieR.FindTrie("192.41.3.1")
if ret != 0 {
  fmt.Printf("Matched prefix %s\n", (*ipn).String())
}
```

# Performance 

Go benchmark currently gives this implementation the following score :

```
llb@nd2:~/lpm$ go test -bench=.
goos: linux
goarch: amd64
pkg: lpm
cpu: Intel(R) Xeon(R) Silver 4210R CPU @ 2.40GHz
BenchmarkTrie-40    	  845660	      1345 ns/op
PASS
ok  	lpm	2.156s
```

