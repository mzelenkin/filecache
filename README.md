Go File Cache
=============

[![Build Status](https://travis-ci.org/DannyBen/filecache.svg?branch=master)](https://travis-ci.org/DannyBen/filecache) [![GoDoc](https://godoc.org/github.com/DannyBen/filecache?status.png)](http://godoc.org/github.com/DannyBen/filecache)


This package provides easy to use, file system cache functions.

Full documentation is at:
[godoc.org/github.com/DannyBen/filecache](http://godoc.org/github.com/DannyBen/filecache)

Install
-------

	$ go get github.com/DannyBen/filecache

Usage
-----

Get the cache handler and set a cache directory and the requested
cache life, in minutes:
	
	handler := filecache.Handler{"./cache", 60}

Store data in the cache by providing a string key to the `Set` method
and `[]byte` data. The key's md5 checksum will be used as the filename.

	data := []byte("Joey doesn't share food")
	handler.Set("testkey", data)

Retrieve data from the cache:
	
	r := handler.Get("testkey")
	if r == nil {
		fmt.Println("Cache has expired")
	} else  {
		fmt.Println(string(r))
	}

