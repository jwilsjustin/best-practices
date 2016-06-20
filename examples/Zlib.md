Using `Zlib` module to create a unique integer

```ruby
"400444#{Zlib.adler32("400444")}".to_i
```

(still need to test and make sure it will be unique)
