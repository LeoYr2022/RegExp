## tcl中如何使用通配符
```tcl
set str "Hello, world!"
if {[string match "Hello,*" $str]} {
    puts "The string starts with 'Hello'."
} else {
    puts "The string does not start with 'Hello'."
}
```
注意使用的是```string match ```

## tcl中如何使用正则表达式
```tcl
set str "Hello, world!"
if {[regexp {^Hello} $str]} {
    puts "The string starts with 'Hello'."
} else {
    puts "The string does not start with 'Hello'."
}
```
注意使用的是 ```regexp```

## 在sdc中没有办法可以匹配“/”
