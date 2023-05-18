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
注意使用的是```string match ```

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
