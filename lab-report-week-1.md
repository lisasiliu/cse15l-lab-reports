# Week 1 Lab Report

**Assignment:** Write a tutorial for incoming 15L students about how to log into a course-specific account on `ieng6`.

---

**Step 1:** Install Visual Studio Code

<img width="397" alt="image" src="https://user-images.githubusercontent.com/44093048/193378371-ca12b159-c4ee-4b82-b644-8b505e612dfe.png">

<sup>_Note: I skipped this step, because VSCode was already installed on my computer (it's my primary IDE)_</sup>

1. Go to this link: https://code.visualstudio.com/
2. Install version for Windows

**Step 2:** Remotely Connecting 

<img width="818" alt="image" src="https://user-images.githubusercontent.com/44093048/193378389-e895ff6a-71bd-4edd-ba23-37d55d79c485.png">

1. Install OpenSSH ([tutorial](https://learn.microsoft.com/en-us/windows-server/administration/openssh/openssh_install_firstuse?tabs=gui)) <sup>_Note: Somehow I already did this prior to the lab, but I assume that the instructions here work._</sup>
2. Connect to the remote host with the command `ssh cs15lfa22[username]@ieng6.ucsd.edu`. ([tutorial](https://code.visualstudio.com/docs/remote/ssh#_connect-to-a-remote-host))
3. Allow it to continue connecting (type 'yes')
4. Enter in your password. (reset it online if it doesn't work)
5. You are now connected to a CSE basement computer!

_--Quick interlude--_

Starting from step 2, everyone in the lab got stuck. Out of about 12-14 people in the aisle, only a grand total of 2 people managed to successfully connect to the server using their university given username (i.e. the one that starts with cs15lfa22)

Hence, I will list the workaround with a 100% success rate that everyone else used.

2. (alt) Connect with the command, `ssh [university-wide username]@ieng6.ucsd.edu'. 

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<sup>_For example, my username in this case was lil043. It's the part before the '@' in your university username_</sup>

Then, continue as usual. All the steps after will work the same!

**Step 3:** Trying Some Commands

<img width="818" alt="image" src="https://user-images.githubusercontent.com/44093048/193378424-c277b9a6-e8b6-4b1d-a345-8fc42164711a.png">

Try whatever commands you want! Common ones include: 
* `cd` (change directory)
* `ls` (list [folder contents])
* `pwd` (print working directory)
* `mkdir` (make a new directory/folder)
* `cp` (copy)

**Step 4:** Moving Files with `scp`

<img width="819" alt="image" src="https://user-images.githubusercontent.com/44093048/193378470-5d9dc89b-ce15-48db-8c6e-3466c624bdb9.png">

`scp`, aka "secure copy", aka the secure version of `cp`

Test this function out with the following sample file (WhereAmI.java) that displays your file path and details about your computer:
```
class WhereAmI {
  public static void main(String[] args) {
    System.out.println(System.getProperty("os.name"));
    System.out.println(System.getProperty("user.name"));
    System.out.println(System.getProperty("user.home"));
    System.out.println(System.getProperty("user.dir"));
  }
}
```

Create it on your computer, and then run the following 2 commands:
1. `javac WhereAmI.java` (compile program)
2. `java WhereAmI` (show results)

Afterwards, use the `scp` command. First parameter is the file name, and the second is the ssh address + the folder you want it in.

Run command:
`scp WhereAmI.java [university-wide username]@ieng6.ucsd.edu:~/` (the ~ just means "home" here)

Then enter the password, and login to ieng6 again with the `ssh` command! Check the file with `ls`, and run the previous 2 commands on the new computer.

<img width="817" alt="image" src="https://user-images.githubusercontent.com/44093048/193378483-f0701a3a-3b35-4428-b557-58474c4c60fe.png">

It should work as perfectly as before; just, the output will be different because the file path on the new computer is different!

**Step 5:** Setting an SSH Key

<img width="819" alt="image" src="https://user-images.githubusercontent.com/44093048/193378505-a5a90df1-e40f-4a2b-bef9-c2ed130d9348.png">

<sup>_Getting rid of your password, very exciting! Notice that in the above screenshot, there is no line saying "Enter Password: "_</sup>

1. Create a pair of `ssh` keys (one public, one private), using the command `ssh-keygen`
2. A key pair will be generated using RSA, which iirc uses prime numbers and is pretty secure/hard to crack.
3. Simply press 'enter' for all 3 prompts (save file, passphrase, passphrase 2.0)

Now, you can use the key files generated to replace the password. The private key is called `id_rsa`, and the public key is called `id_rsa.pub`). You can copy the public key to the other server with the following steps:

1. Use `ssh` to get on the other server
2. Create the folder, `.ssh` (command: `mkdir .ssh`), where your keys will be stored
3. Logout of the other server
4. Now, use `scp`, with the first parameter (what to copy) being `id_rsa.pub` and the second parameter (where to copy) being `[university-wide username]@ieng6.ucsd.edu:~/.ssh/authorized_keys`

Now, try `ssh` again! It should no longer require you to type your password in.

**Step 6:** Optimizing Remote Running

<img width="794" alt="image" src="https://user-images.githubusercontent.com/44093048/193378534-8f71f5e2-5369-4030-83a6-d0374af18451.png">

My advice, in a nutshell: press 'tab' to auto-fill words whenever possible.

For example, if the only file that starts with a 'W' is WhereAmI.java, you can type W + tab, and WhereAmI.java should be filled in automatically! This saves lots of time over repetition.

Similarly, learn keyboard shortcuts and ways to condense commands.

