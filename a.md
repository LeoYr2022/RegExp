## 通配符和正则表达式在TCL中的举例
### tcl中使用通配符
```tcl
set str "Hello, world!"
if {[string match "Hello,*" $str]} {
    puts "The string starts with 'Hello'."
} else {
    puts "The string does not start with 'Hello'."
}
```
- 注意使用的是```string match ```
- ? 通配符可以匹配一个字符
- *通配符表示可以包含任意数量的字符（包括零个字符）
- [] 来指定一个字符集，以及 ^ 符号来指定一个否定字符集
- 在 TCL 的许多命令和函数中都可以使用通配符，例如 string match、regexp、glob 等等
### glob使用举例
``` tcl
set path {/home/user/documents/{project1,project2}/*.txt}
foreach file [glob -nocomplain $path] {
   puts $file
}
```

### tcl中使用正则表达式
```tcl
set str "Hello, world!"
if {[regexp {^Hello} $str]} {
    puts "The string starts with 'Hello'."
} else {
    puts "The string does not start with 'Hello'."
}
```
注意使用的是 ```regexp```

## 通配符和正则表达式在sdc中的举例
### sdc中使用通配符
```sdc
create_clock -name clk1 -period 10 [get_ports {clk}]
create_clock -name clk2 -period 20 [get_ports {clk}]
create_clock -name clk3 -period 30 [get_ports {clk}]
create_clock -name clk4 -period 40 [get_ports {other_clk}]
set_clock_groups -name clk_group [get_clocks "/top/*clk*"]
```

### sdc中使用正则表达式
```sdc
create_clock -name clk1 -period 10 [get_ports {clk}]
create_clock -name clk2 -period 20 [get_ports {clk}]
create_clock -name clk3 -period 30 [get_ports {clk}]
create_clock -name clk4 -period 40 [get_ports {other_clk}]
set_clock_groups -name clk_group [get_clocks [regexp {.*clk[1-3]$} [get_clocks]]]
```
