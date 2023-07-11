
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
  
  ![Screenshot from 2023-07-09 00-21-19](https://github.com/aaryangupta/VSD-TCL-workshop/assets/40055877/24a03c4f-e958-480d-9ce8-85c99db39e87)

* user enters the wrong csv file/ file doesnt exist
  ![Screenshot from 2023-07-09 00-21-52](https://github.com/aaryangupta/VSD-TCL-workshop/assets/40055877/c75dcb50-090b-4064-9315-9b7e050cceb3)


* user enters -help
![Screenshot from 2023-07-09 00-22-18](https://github.com/aaryangupta/VSD-TCL-workshop/assets/40055877/0087c5c0-da6d-4475-8283-be8778ff312c)


## Day-2

Convert all inputs to format-y and SDC format and pass them to Yosys tool

Task we will perform are as :
* Creating the variables
* check if files and directories mentioned in csv exists or not
* Read constraints file in csv and convert to SDC format
* Read all the files in netlist directory
* create main synthesis script into format 2
* pass that script to Yosys

> Creating variables
![Screenshot from 2023-07-09 19-17-21](https://github.com/aaryangupta/VSD-TCL-workshop/assets/40055877/7b00a587-32de-432f-a404-92db1c75d39e)


>Check the prescence of paths and names
![Screenshot from 2023-07-09 19-17-32](https://github.com/aaryangupta/VSD-TCL-workshop/assets/40055877/1b09a23c-5a8b-45c5-af5f-0278bb686a2e)


>return error if the required parameters are not present
![Screenshot from 2023-07-10 01-36-54](https://github.com/aaryangupta/VSD-TCL-workshop/assets/40055877/41cad8f6-93c3-4b5a-b4fc-934b6822a79d)

 
>Read the Constraint file and proccess parameters for the SDC file
![Screenshot from 2023-07-10 01-51-59](https://github.com/aaryangupta/VSD-TCL-workshop/assets/40055877/8e581b42-9b78-4301-a7be-b937ea2c12f3)


## Day-3

Countinue from day 2 task, Read Constraints.csv file and convert to sdc format

getting clock details from csv file and writing it the sdc file in the required format
Note: need to identify bussed and non bussed inputs and outputs before entering in the required format.

>The file named openMSP430_design_details.csv appears as follows:
![Screenshot from 2023-07-11 02-33-35](https://github.com/aaryangupta/VSD-TCL-workshop/assets/40055877/3a7feac3-31d0-4b88-b9d8-4237e3af14a3)
![Screenshot from 2023-07-11 02-37-00](https://github.com/aaryangupta/VSD-TCL-workshop/assets/40055877/9e66cd3f-87c7-4016-8265-47a37c3ec6e3)

>getting input details from csv file and writing it in the required format
![Screenshot from 2023-07-11 03-11-51](https://github.com/aaryangupta/VSD-TCL-workshop/assets/40055877/2a350409-045a-4fc5-a313-05fe6d2e4bc2)

>getting output details from csv file and writing it in the required format
![Screenshot from 2023-07-11 03-38-07](https://github.com/aaryangupta/VSD-TCL-workshop/assets/40055877/4828e6c9-6868-41e8-b1fb-ab20fa6c1335)


>A snip of the sdc file
![Screenshot from 2023-07-11 03-20-12](https://github.com/aaryangupta/VSD-TCL-workshop/assets/40055877/f1cc4b51-6d52-490a-afe0-4fec208763af)



## Day-4

YOSYS (Yosys Open SYnthesis Suite)
YOSYS is a highly regarded open-source framework for RTL synthesis and formal verification of digital circuits. It operates by taking RTL descriptions, such as Verilog, as input and then proceeds to perform synthesis, ultimately generating a netlist at the gate level. YOSYS provides robust support for crucial tasks like technology mapping, optimization, and formal verification. Its versatility is further enhanced by a scripting interface, enabling seamless integration with other EDA (Electronic Design Automation) tools. As a result, YOSYS has gained substantial popularity and finds extensive usage in both academic and industrial settings for various digital design endeavors.

Tasks:
* Checking the Hierarchy
* Error handling

>To begin, retrieve the netlist and store it in a variable named "data" as shown:
![Screenshot from 2023-07-11 03-57-38](https://github.com/aaryangupta/VSD-TCL-workshop/assets/40055877/099abcbf-bb30-4061-8054-1279a420b4f7)

>running hierarchy check
![Screenshot from 2023-07-11 14-07-41](https://github.com/aaryangupta/VSD-TCL-workshop/assets/40055877/50a24d55-ad41-4abe-b94b-cfed70d13818)

>After making a unknown module in openMsp430.v file ...
![Screenshot from 2023-07-11 14-10-20](https://github.com/aaryangupta/VSD-TCL-workshop/assets/40055877/e9536bb5-b857-4a08-9efc-3c126127a4a5)

> referenced in module error due to calling incorrectly or module doesnt exist
![Screenshot from 2023-07-11 14-10-41](https://github.com/aaryangupta/VSD-TCL-workshop/assets/40055877/a6bd37ac-0917-4cc5-9573-22f6b20d445e)

>checking logs by following command:
![Screenshot from 2023-07-11 14-13-35](https://github.com/aaryangupta/VSD-TCL-workshop/assets/40055877/845afdcd-a256-4f03-a0a4-1c85035e60e1)
![Screenshot from 2023-07-11 14-13-19](https://github.com/aaryangupta/VSD-TCL-workshop/assets/40055877/958e6634-fa13-4122-a632-a29c4de1a124)


![Screenshot from 2023-07-11 14-21-15](https://github.com/aaryangupta/VSD-TCL-workshop/assets/40055877/6e9a24c1-a5b2-4db8-899d-85ce308dcd74)

![Screenshot from 2023-07-11 14-22-54](https://github.com/aaryangupta/VSD-TCL-workshop/assets/40055877/63c77df2-ce25-49b3-9ef6-bd766ae27291)

![Screenshot from 2023-07-11 14-23-24](https://github.com/aaryangupta/VSD-TCL-workshop/assets/40055877/4b9eef7c-e493-49f0-812b-885e1eb2edf1)

![Screenshot from 2023-07-11 14-25-00](https://github.com/aaryangupta/VSD-TCL-workshop/assets/40055877/4aebe01a-2932-487e-8281-9d58aba25bb4)

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

![Screenshot from 2023-07-11 17-23-25](https://github.com/aaryangupta/VSD-TCL-workshop/assets/40055877/dcfa383b-6edd-4ce9-bffa-f90662300808)
![Screenshot from 2023-07-11 17-32-40](https://github.com/aaryangupta/VSD-TCL-workshop/assets/40055877/517a22d4-e6b6-47ec-82fd-bdfaf97e34da)

![Screenshot from 2023-07-11 17-46-51](https://github.com/aaryangupta/VSD-TCL-workshop/assets/40055877/bc9db152-46ac-44fe-b787-e49c247c443f)

![Screenshot from 2023-07-11 18-09-23](https://github.com/aaryangupta/VSD-TCL-workshop/assets/40055877/016ade03-8eb4-412f-93b9-28627f77a49c)
![Screenshot from 2023-07-11 18-12-08](https://github.com/aaryangupta/VSD-TCL-workshop/assets/40055877/c6e36b25-2c66-4de2-9b7d-d8c9c03ed6fe)
![Screenshot from 2023-07-11 18-26-02](https://github.com/aaryangupta/VSD-TCL-workshop/assets/40055877/ee0daf49-d73a-411f-8376-cdc12aa32f1a)
![Screenshot from 2023-07-11 18-49-37](https://github.com/aaryangupta/VSD-TCL-workshop/assets/40055877/90b5530a-c011-4708-836b-7abcc29b70e5)
![Screenshot from 2023-07-11 19-00-46](https://github.com/aaryangupta/VSD-TCL-workshop/assets/40055877/8406fc59-0a6d-4ad4-a751-dcb264181426)

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


