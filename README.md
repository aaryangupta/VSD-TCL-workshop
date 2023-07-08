
# VSD-TCL-Workshop From Introduction to Advanced Scripting Techniques in Design and Synthesis

TCL, short for Tool Command Language, is a dynamic scripting language renowned for its application in scripting, automation, and rapid prototyping. In TCL, all forms of data, commands, and even programming constructs are represented as strings. This unique approach grants TCL a remarkable level of flexibility, empowering users with powerful string manipulation capabilities.

At the heart of TCL lies its command-centric nature. TCL commands play a pivotal role in executing operations and manipulating data. The language offers a comprehensive set of built-in commands tailored for diverse tasks, including file handling, string manipulation, control flow, and mathematical operations.

TCL's appeal stems from its simplicity, flexibility, and seamless integration capabilities. These qualities make it an incredibly versatile scripting language suitable for a wide array of applications and domains.




## Day -1

Before executing the command in the terminal, please ensure that you have provided the necessary permissions to it by using the appropriate command.

```bash
  chmod +x filename
```

Create Command (aaryan) and pass csv file from UNIC shell to Tcl script

1. To create command , we need to run first-

```bash
  vim commandname #commandname=whatever you like
```
after thar a window will open, press "i", you will see insert text in left side. Then write the script.

In script, most importent lines, will explain to you--

```bash
  #!/bin/tcsh -f  
```
you need to write this line to tell system, that it is a script file.

In last of script file, you need to write-
```bash
  tclsh pandabro.tcl $argv[1] 
```
to source the Unix shell to the Tcl script by passing the required csv file.

Now we will see three diffrent scenario-

* user doesnt enter the csv file

* user enters the wrong csv file/ file doesnt exist

* user enters -help


## Day-2

Converting inputs to format[1] and feeding it to yosys for synthesis

* Create Variables

* Checking if the directories exist or not ( done to prevent the script from breaking )

* Displays an error when the required file is not in the needed directory


## Day-3

Read Constraints.csv file and convert to sdc format

getting clock details from csv file and writing it the sdc file in the required format
getting input details from csv file and writing it in the required format
getting output details from csv file and writing it in the required format
Note: need to identify bussed and non bussed inputs and outputs before entering in the required format.

The script writing the sdc constraints.


A snip of the sdc file


## Day-4

YOSYS (Yosys Open SYnthesis Suite)
YOSYS is a highly regarded open-source framework for RTL synthesis and formal verification of digital circuits. It operates by taking RTL descriptions, such as Verilog, as input and then proceeds to perform synthesis, ultimately generating a netlist at the gate level. YOSYS provides robust support for crucial tasks like technology mapping, optimization, and formal verification. Its versatility is further enhanced by a scripting interface, enabling seamless integration with other EDA (Electronic Design Automation) tools. As a result, YOSYS has gained substantial popularity and finds extensive usage in both academic and i
ndustrial settings for various digital design endeavors.

Creating scripts for synthesis and running it on yosys

creating script for Hierarchy check
running hierarchy check

Case 1: When all the modules are present and called correctly


Case 2: referenced in module error due to calling incorrectly or module doesnt exist


* after the hierarchy check is passed . The main synthesis script is written.
* running synthesis if there are no error in hierarchy check.

Case 1: No error in hierarchy


Case 2: error encountered in hierarchy



## Day - 5

create script for OpenTimer and run STA analysis followed by generation of Quality of Results (QoR)

To generate a script for OpenTimer, you can utilize procs. Procs, short for procedures, are external TCL files that execute specific operations when sourced into the main TCL script. They function similarly to functions in Python programming.

For example, you can create a proc called "read_liberty" which accepts arguments like "-lib", "-late", "-early", and "/or". This proc will perform specific actions based on the provided arguments when sourced into the main TCL script. By referencing the proc and mapping the arguments to the external TCL script (proc script), the "read_liberty" command will be executed.

After executing the proc command, the main TCL script will contain the output or result of the proc, which can be further utilized as needed.

Using procs in this manner allows for modular and reusable code, enhancing the flexibility and functionality of the OpenTimer script generation process.

To gain a visual understanding, please refer to the accompanying image illustrating the concepts described.


* Entering the world of procs
1. reopenStdout.proc

```bash
  proc reopenStdout {file} {
  #closes the main terminal window where all the puts statements were being displayed as info to user
  close stdout
  #opens $file in write mode
  open $file w       
}
```

The "reopenStdout" proc serves a straightforward purpose of closing the standard output (stdout) of the main terminal and opening a file in write mode.

2. set_num_threads.proc
```bash
  proc set_multi_cpu_usage {args} {
    array set options {-localCpu <num_of_threads> -help "" }
    foreach {switch value} [array get options] {
    puts "Option $switch is $value"
    }
    while {[llength $args]} {
    puts "llength is [llength $args]"
    puts "lindex 0 of \"$args\" is [lindex $args 0]"
        switch -glob -- [lindex $args 0] {
          -localCpu {
              puts "old args is $args"
              set args [lassign $args - options(-localCpu)]
              puts "new args is \"$args\""
              puts "set_num_threads $options(-localCpu)"
              }
          -help {
              puts "old args is $args"
              set args [lassign $args - options(-help) ]
              puts "new args is \"$args\""
              puts "Usage: set_multi_cpu_usage -localCpu <num_of_threads>"
              }
        }
    }
}
```


