Download Link: https://assignmentchef.com/product/solved-ee328-operating-system-7
<br>



<h1>Simple Shell</h1>




<h2>1 PROBLEM</h2>

<h3>1.1 DESCRIPTION</h3>

Write a program that can imitate a simple shell and execute some basic commands. You can see the detail in the end of chapter 3 of <em>OPERATING SYSTEM CONCEPTS WITH JAVA(Seventh Edition)</em>, page 127.

<h2>2 ALGORITHM</h2>

<h3>2.1 SHELL INTERFACE</h3>

The key is to create an external process to let the Linux operating system to help execute most of the command based on its command document in the Linux. So this program can only be executed in the OS like Linux other than Windows because the command in Linux is in Command documents. This kind of commands is like <em>ls, cat, pwd</em>. What we need to do is to read in user’s commands and transmit them to Linux Command Documents.

Some commands in the requirements like <em>cd, history, ! and exit </em>are not in the system, and we have to implement them by ourselves.

<h3>2.2 IMPLEMENTATION OF <em>cd</em></h3>

This command includes a few operations. For instance,

<table width="322">

 <tbody>

  <tr>

   <td width="306"><em>cd </em>..</td>

   <td width="16">(1)</td>

  </tr>

  <tr>

   <td width="306"><em>cd </em>/<em>usr</em>/<em>bin</em></td>

   <td width="16">(2)</td>

  </tr>

  <tr>

   <td width="306"><em>cd src</em></td>

   <td width="16">(3)</td>

  </tr>

 </tbody>

</table>

Thus we need to get the current directory using <em>getProperty() </em>first. For (1) we can get the directory by wiping out the last file. But if the current directory has already been <em>root</em>, the directory has to be set as “/”. For (2) and (3), we need to judge whether the directory is legal or not by <em>isDirectory()</em>. Then we replace the directory according to the command for (2) or add the folder after current directory for (3).

<h3>2.3 IMPLEMENTATION OF <em>history</em></h3>

This command is implemented with the help of <em>ArrayList</em>. Every time the user input something we can save it into an <em>ArrayList </em>as long as it’s not the same as the last one. When the user input <em>history </em>the commands stored in the <em>ArrayList </em>will be printed with an order number.

If the user input “!!”, the last command will be executed automatically. In the meantime “!” with a command number i leads to the execution of the ith last command. In addition, if there is more characters after “!!” they will be concatenated to the last command. For example if the last command is <em>ls </em>and the user input <em>!! -l</em>, the shell actually executes <em>ls -l</em>.

<h3>2.4 ROBUSTNESS CONSIDERATION</h3>

If the user input is illegal a <em>IOException </em>will be thrown. The shell interface will give out an error message and continue to work until an <em>exit </em>is input to terminate the shell.

<h2>3 RESULTS</h2>

<h3>3.1 ENVIRONMENT</h3>

<ul>

 <li>Ubuntu 14.04 LTS</li>

 <li>Java Development Kit 1.8.0_131</li>

 <li>Eclipse</li>

</ul>

3.2 SCREENSHOTS OF THE RESULT

We use Linux Terminal to compile and execute the program. The result is shown in Fig. 3.1.

<h3>3.3 THOUGHTS</h3>

It is the first time I use an coding environment under Linux. The process of encountering the problems and addressing them is very challenging and helps me a lot.

Figure 3.1: Screenshot of Simple Shell Interface