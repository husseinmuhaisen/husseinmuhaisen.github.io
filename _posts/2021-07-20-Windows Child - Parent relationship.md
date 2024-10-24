<div style="clear: both; text-align: center;"><a href="https://1.bp.blogspot.com/-WOszlVUYXDY/YPacCqhHF6I/AAAAAAAAABc/cyX9QpcQgX0D88yYqqQVMN0St6y51sFmwCLcBGAsYHQ/s1200/windowsssssssssss.png" style="margin-left: 1em; margin-right: 1em;"><img border="0" data-original-height="600" data-original-width="1200" height="367" src="https://1.bp.blogspot.com/-WOszlVUYXDY/YPacCqhHF6I/AAAAAAAAABc/cyX9QpcQgX0D88yYqqQVMN0St6y51sFmwCLcBGAsYHQ/w618-h367/windowsssssssssss.png" width="618" /></a></div>
<h2 style="text-align: left;"></h2>
<p style="text-align: left;">Each Process in the Windows operating system points to its parent process which is basically the creator process. However, if the creator process or what so-called parent process is killed, the Information related to that process won't be updated therefore the child process might refer to a non-existent process.</p>
<h3 style="text-align: left;"></h3>
We will be conducting an experiment to show the Child/Parent process relationship in Windows. So let's prove that windows don't keep track of not more than 1 parent process ID.
Let's demonstrate a simple process list first before we dive into the example
<ol style="text-align: left;">
 	<li><b>press "WIN + R"</b></li>
 	<li><b>type "cmd"</b></li>
 	<li><b>press "Enter"</b></li>
 	<li><b>type "tasklist /svc"</b></li>
</ol>
You should get a long list of running processes as shown in the following image:
<div>
<div>
<div style="clear: both; text-align: center;"><a href="https://lh3.googleusercontent.com/-KufDEapb2Tc/YPadcGgA5jI/AAAAAAAAABs/pqe3CSNYb0Y-YAw4KCkv70pih-yYQ0U-QCLcBGAsYHQ/Process-CMD.png" style="margin-left: 1em; margin-right: 1em;"><img alt="" data-original-height="984" data-original-width="723" height="640" src="https://lh3.googleusercontent.com/-KufDEapb2Tc/YPadcGgA5jI/AAAAAAAAABs/pqe3CSNYb0Y-YAw4KCkv70pih-yYQ0U-QCLcBGAsYHQ/w469-h640/Process-CMD.png" width="469" /></a></div>
<b>As you can see the list above shows the parent/child process relationship, so as you can see windows maintains the processes by assigning Process IDs (PID),  we have multiple running processes, windows won't be able to identify the process of the process creator because windows only maintain and identifies the creator process ID. To prove that windows don't keep track of more than just the parent process ID. I will be showing you an example.</b></div>
<div><b>
</b></div>
<ol style="text-align: left;">
 	<li><b>press "WIN+R"</b></li>
 	<li><b>type "cmd"</b></li>
 	<li><b>press "Enter"</b></li>
 	<li><b>type "title parent"</b></li>
  <li><b>type "start cmd</b></li>
 	<li>
<p style="box-sizing: inherit; grid-column: main-start / main-end; margin: 45px 0px 0px;"><span style="color: #333333; font-family: Muli, sans-serif;"><span style="background-color: white; font-weight: 400;">"</span></span></p>
</li>
</ol>
<b>
<div style="clear: both; text-align: center;"><a href="https://lh3.googleusercontent.com/-eYGhVpNDpos/YPaeGBWa6_I/AAAAAAAAAB0/u5EWVxDHyLAQUiEm2PLpYqfTX2tGIN6_ACLcBGAsYHQ/title-parent.png" style="margin-left: 1em; margin-right: 1em;"><img alt="" data-original-height="134" data-original-width="291" height="184" src="https://lh3.googleusercontent.com/-eYGhVpNDpos/YPaeGBWa6_I/AAAAAAAAAB0/u5EWVxDHyLAQUiEm2PLpYqfTX2tGIN6_ACLcBGAsYHQ/w400-h184/title-parent.png" width="400" /></a></div>
</b>
<p style="background-color: white; box-sizing: inherit; color: #333333; font-family: Muli, sans-serif; font-size: 16px; grid-column: main-start / main-end; margin: 20px 0px 0px;">
<p style="background-color: white; box-sizing: inherit; color: #333333; font-family: Muli, sans-serif; font-size: 16px; grid-column: main-start / main-end; margin: 20px 0px 0px;">
<div style="clear: both; text-align: center;"><a href="https://lh3.googleusercontent.com/-cGRMEPhPRXg/YPaedgfvw5I/AAAAAAAAAB8/dESVTSmeimM_7trhB0e-X8H5cwBmuoacQCLcBGAsYHQ/new_cmd.png" style="margin-left: 1em; margin-right: 1em;"><img alt="" data-original-height="540" data-original-width="1107" height="312" src="https://lh3.googleusercontent.com/-cGRMEPhPRXg/YPaedgfvw5I/AAAAAAAAAB8/dESVTSmeimM_7trhB0e-X8H5cwBmuoacQCLcBGAsYHQ/w640-h312/new_cmd.png" width="640" /></a></div>
</div>
<b>As you can see we spawned another cmd from the first cmd we have launched that we named "parent"</b></p>

<div style="text-align: left;"></div>
<div>6.<b>type "title child"</b></div>
<div><b>
<div style="clear: both; text-align: center;"><a href="https://lh3.googleusercontent.com/-P36-bClG-O8/YPaeyfiNcZI/AAAAAAAAACE/OJMDjenFvgMi6UrL0MxNRGfSh2svWnKUACLcBGAsYHQ/title_child.png" style="margin-left: 1em; margin-right: 1em;"><img alt="" data-original-height="130" data-original-width="257" height="203" src="https://lh3.googleusercontent.com/-P36-bClG-O8/YPaeyfiNcZI/AAAAAAAAACE/OJMDjenFvgMi6UrL0MxNRGfSh2svWnKUACLcBGAsYHQ/w400-h203/title_child.png" width="400" /></a></div>
7. type "mspaint" in the child command prompt to launch Microsoft paint.</b>
<div></div>
</div>
<div></div>
<div>
<div style="clear: both; text-align: center;"><a href="https://lh3.googleusercontent.com/-geNUd79TnqQ/YPae9_vU3eI/AAAAAAAAACI/NCXvTwKUROoW1Zmq8DHO5hxxVs8rkaceACLcBGAsYHQ/ms_paint.png" style="margin-left: 1em; margin-right: 1em;"><img alt="" data-original-height="271" data-original-width="1032" height="168" src="https://lh3.googleusercontent.com/-geNUd79TnqQ/YPae9_vU3eI/AAAAAAAAACI/NCXvTwKUROoW1Zmq8DHO5hxxVs8rkaceACLcBGAsYHQ/w640-h168/ms_paint.png" width="640" /></a></div>
<b>

8. Now close the child command prompt by typing in "exit".

After you do that you will notice that Microsoft paint remains open even tho we have closed the terminal we spawned it from.

9. Launch your task manager, you can do that by pressing " CTRL + Shift +Esc".

10.Locate the cmd process we have running which falls under the name "parent"</b></div>
<div></div>
<div>
<div style="clear: both; text-align: center;"><a href="https://lh3.googleusercontent.com/-UmascXI4tqQ/YPafJsfnaBI/AAAAAAAAACQ/pKB0DV55NS0sVRnBttxFXDWCCVMMgh1-wCLcBGAsYHQ/parent.png" style="margin-left: 1em; margin-right: 1em;"><img alt="" data-original-height="784" data-original-width="902" height="557" src="https://lh3.googleusercontent.com/-UmascXI4tqQ/YPafJsfnaBI/AAAAAAAAACQ/pKB0DV55NS0sVRnBttxFXDWCCVMMgh1-wCLcBGAsYHQ/w640-h557/parent.png" width="640" /></a></div>
</div>
<div></div>
<b><span>&nbsp;&nbsp; &nbsp;</span><span>&nbsp;&nbsp; &nbsp;</span><span>&nbsp;&nbsp; &nbsp;</span><span>&nbsp;&nbsp; &nbsp;</span><span>&nbsp;&nbsp; &nbsp;</span><span>&nbsp;&nbsp; &nbsp;</span><span>&nbsp;&nbsp; &nbsp;</span><span>&nbsp;&nbsp; &nbsp;</span><span>&nbsp;&nbsp; &nbsp;</span><span>&nbsp;&nbsp; &nbsp;</span>As you can see the parent process is shown.

11. Right-click the Windows Command Processor then click on Go to Details.</b>
<div>
<div style="clear: both; text-align: center;"><a href="https://lh3.googleusercontent.com/-Soumzu3-b0Q/YPafXqiJskI/AAAAAAAAACY/3NBLSEviXrECkwEcAyrZ5ot2U42NVzKPwCLcBGAsYHQ/details.png" style="margin-left: 1em; margin-right: 1em;"><img alt="" data-original-height="904" data-original-width="431" height="640" src="https://lh3.googleusercontent.com/-Soumzu3-b0Q/YPafXqiJskI/AAAAAAAAACY/3NBLSEviXrECkwEcAyrZ5ot2U42NVzKPwCLcBGAsYHQ/w304-h640/details.png" width="304" /></a></div>
<b>12.Right-click the cmd.exe process and select End process tree. this will terminate all processes in the tree

As you can see the "parent" command prompt will disappear but MSPaint will still be running because it was the grandchild of the process we have terminated which is the whole tree that had the "parent" cmd process meaning that MSPaint is the grandchild of the parent process. Because the intermediate process was killed, there was no link between the parent and the grandchild.

I really hope you guys enjoyed this basic little article I wrote and this might come in handy for some people out there I just wanted to blog this thing about windows :)

Hussein A. Muhaisen</b></div>
<div>
<div></div>
<div></div>
<div></div>
<div></div>
</div>
