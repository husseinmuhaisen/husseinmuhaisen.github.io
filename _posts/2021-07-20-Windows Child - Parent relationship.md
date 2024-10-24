<!DOCTYPE html>
<html>
<head>
  <meta charset="UTF-8">
  <title>Understanding Parent and Child Processes in Windows</title>
</head>
<body>
  <h1 style="text-align: center;">Understanding Parent and Child Processes in Windows</h1>

  <div style="text-align: center;">
    <a href="https://1.bp.blogspot.com/-WOszlVUYXDY/YPacCqhHF6I/AAAAAAAAABc/cyX9QpcQgX0D88yYqqQVMN0St6y51sFmwCLcBGAsYHQ/s1200/windowsssssssssss.png" style="margin-left: 1em; margin-right: 1em;">
      <img src="https://1.bp.blogspot.com/-WOszlVUYXDY/YPacCqhHF6I/AAAAAAAAABc/cyX9QpcQgX0D88yYqqQVMN0St6y51sFmwCLcBGAsYHQ/w618-h367/windowsssssssssss.png" alt="Windows Processes" width="618" height="367" />
    </a>
  </div>

  <p>Each process in the Windows operating system points to its parent process, which is basically the creator process. However, if the creator process, or what is called the parent process, is terminated, the information related to that process won't be updated. Therefore, the child process might refer to a non-existent process.</p>

  <h2>Demonstrating the Parent-Child Process Relationship</h2>

  <p>We will be conducting an experiment to show the child/parent process relationship in Windows. Let's prove that Windows doesn't keep track of more than one parent process ID.</p>

  <p>First, let's demonstrate a simple process list before we dive into the example:</p>

  <ol>
    <li><b>Press "WIN + R".</b></li>
    <li><b>Type "cmd".</b></li>
    <li><b>Press "Enter".</b></li>
    <li><b>Type <code>tasklist /svc</code>.</b></li>
  </ol>

  <p>You should get a long list of running processes, as shown in the following image:</p>

  <div style="text-align: center;">
    <img src="https://lh3.googleusercontent.com/-KufDEapb2Tc/YPadcGgA5jI/AAAAAAAAABs/pqe3CSNYb0Y-YAw4KCkv70pih-yYQ0U-QCLcBGAsYHQ/w469-h640/Process-CMD.png" alt="Process List in CMD" width="469" height="640" />
  </div>

  <p>As you can see, the list above shows the processes running on your system. Windows maintains processes by assigning Process IDs (PIDs). We have multiple running processes, but Windows won't be able to identify the process of the process creator beyond the immediate parent because it only maintains and identifies the creator process ID. To prove that Windows doesn't keep track of more than just the parent process ID, I will show you an example.</p>

  <h3>The Experiment</h3>

  <ol>
    <li><b>Press "WIN + R".</b></li>
    <li><b>Type <code>cmd</code>.</b></li>
    <li><b>Press "Enter".</b></li>
    <li><b>Type <code>title parent</code> and press "Enter".</b></li>
    <li><b>Type <code>start cmd</code> and press "Enter".</b></li>
    <li><b>In the new command prompt window, type <code>title child</code> and press "Enter".</b></li>
    <li><b>Type <code>mspaint</code> to launch Microsoft Paint and press "Enter".</b></li>
    <li><b>Close the child command prompt by typing <code>exit</code> and pressing "Enter".</b></li>
  </ol>

  <p>As you can see, we spawned another command prompt from the first one we launched, which we named "parent".</p>

  <div style="text-align: center;">
    <img src="https://lh3.googleusercontent.com/-eYGhVpNDpos/YPaeGBWa6_I/AAAAAAAAAB0/u5EWVxDHyLAQUiEm2PLpYqfTX2tGIN6_ACLcBGAsYHQ/w400-h184/title-parent.png" alt="Command Prompt Titled 'parent'" width="400" height="184" />
  </div>

  <p>The new command prompt window titled "child" appears:</p>

  <div style="text-align: center;">
    <img src="https://lh3.googleusercontent.com/-cGRMEPhPRXg/YPaedgfvw5I/AAAAAAAAAB8/dESVTSmeimM_7trhB0e-X8H5cwBmuoacQCLcBGAsYHQ/w640-h312/new_cmd.png" alt="New Command Prompt Window" width="640" height="312" />
  </div>

  <p>We set the title of this command prompt to "child":</p>

  <div style="text-align: center;">
    <img src="https://lh3.googleusercontent.com/-P36-bClG-O8/YPaeyfiNcZI/AAAAAAAAACE/OJMDjenFvgMi6UrL0MxNRGfSh2svWnKUACLcBGAsYHQ/w400-h203/title_child.png" alt="Command Prompt Titled 'child'" width="400" height="203" />
  </div>

  <p>Then, we launched Microsoft Paint by typing <code>mspaint</code> in the child command prompt:</p>

  <div style="text-align: center;">
    <img src="https://lh3.googleusercontent.com/-geNUd79TnqQ/YPae9_vU3eI/AAAAAAAAACI/NCXvTwKUROoW1Zmq8DHO5hxxVs8rkaceACLcBGAsYHQ/w640-h168/ms_paint.png" alt="Microsoft Paint Launched" width="640" height="168" />
  </div>

  <p>Now, close the child command prompt by typing <code>exit</code>. After you do that, you will notice that Microsoft Paint remains open even though we have closed the terminal we spawned it from.</p>

  <p>Next, launch your Task Manager by pressing "CTRL + Shift + Esc".</p>

  <p>Locate the <code>cmd</code> process we have running, which is titled "parent":</p>

  <div style="text-align: center;">
    <img src="https://lh3.googleusercontent.com/-UmascXI4tqQ/YPafJsfnaBI/AAAAAAAAACQ/pKB0DV55NS0sVRnBttxFXDWCCVMMgh1-wCLcBGAsYHQ/w640-h557/parent.png" alt="Parent Command Prompt in Task Manager" width="640" height="557" />
  </div>

  <p>As you can see, the parent process is displayed.</p>

  <p>Right-click the Windows Command Processor, then click on "Go to Details".</p>

  <div style="text-align: center;">
    <img src="https://lh3.googleusercontent.com/-Soumzu3-b0Q/YPafXqiJskI/AAAAAAAAACY/3NBLSEviXrECkwEcAyrZ5ot2U42NVzKPwCLcBGAsYHQ/w304-h640/details.png" alt="Go to Details in Task Manager" width="304" height="640" />
  </div>

  <p>Right-click the <code>cmd.exe</code> process and select "End process tree". This will terminate all processes in the tree.</p>

  <p>As you can see, the "parent" command prompt will disappear, but Microsoft Paint will still be running because it was the grandchild of the process we terminated. Since the intermediate process was killed, there was no link between the parent and the grandchild.</p>

  <p>I really hope you enjoyed this basic little article I wrote. This might come in handy for some people out there. I just wanted to share this information about Windows. :)</p>

  <p><b>Hussein A. Muhaisen</b></p>
</body>
</html>
