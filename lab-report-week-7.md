# Week 7 Lab Report

**Assignment:** Instructions [here](https://ucsd-cse15l-f22.github.io/week/week7/).

---

### Part 1: start -> base

**Task:** Change the name of the `start` parameter and its uses to `base`

_Commands:_ `/start<Enter>dwibase<Esc>/start<Enter>dwibase<Esc>/start<Enter>dwibase<Esc>:wq<Enter>`

**1.** `/start<Enter>`

<img width="868" alt="image" src="https://user-images.githubusercontent.com/44093048/201580038-04aa9399-f9af-48b4-b88b-9040a7f81d42.png">

Cursor moves to start of the first occurence of 'start' it finds.

**2.** `dw`

<img width="864" alt="image" src="https://user-images.githubusercontent.com/44093048/201580263-05042c1e-3a5f-4f26-9b00-b615fbd5e123.png">

Word 'start' is deleted.

**3.** `ibase<Esc>`

<img width="869" alt="image" src="https://user-images.githubusercontent.com/44093048/201580649-07a76c0c-3c13-4a8d-b599-3ff9281cf6a9.png">

Entering insert mode, adding the word 'base', and then returning to normal mode.

**4.** `/start<Enter>`

Same as step 1, except with the 'start' here: 

<img width="866" alt="image" src="https://user-images.githubusercontent.com/44093048/201580949-1d54b660-6fce-4f8a-b591-cfe25a9b174f.png">

Cursor moves to start of the first occurence of 'start' it finds.

**5.** `dw`

<img width="862" alt="image" src="https://user-images.githubusercontent.com/44093048/201581011-fc63620d-60ce-44f2-ab7b-8f179696923d.png">

Word 'start' is deleted.

**6.** `ibase<Esc>`

<img width="866" alt="image" src="https://user-images.githubusercontent.com/44093048/201581068-9c73bc53-6bc7-4079-8853-f4b4b23a3c9e.png">

Entering insert mode, adding the word 'base', and then returning to normal mode.


**7.** `/start<Enter>`

<img width="863" alt="image" src="https://user-images.githubusercontent.com/44093048/201581144-abf8c996-72e3-4e88-9852-ba72b5fc9d65.png">

Last (relevant) 'start' is found.

Cursor moves to start of the first occurence of 'start' it finds.

**8.** `dw`

<img width="865" alt="image" src="https://user-images.githubusercontent.com/44093048/201581208-c319e9af-3703-4ada-a2cd-f7ac200b23c5.png">

Word 'start' is deleted.

**9.** `ibase<Esc>`

<img width="866" alt="image" src="https://user-images.githubusercontent.com/44093048/201581237-c3ebb323-2245-4dc4-8866-ebf679700973.png">

Entering insert mode, adding the word 'base', and then returning to normal mode.

**10.** `:wq<Enter>`

<img width="868" alt="image" src="https://user-images.githubusercontent.com/44093048/201581324-0cca56f0-fbc1-4832-ba3f-93c5047feb06.png">
<img width="749" alt="image" src="https://user-images.githubusercontent.com/44093048/201581353-b64e652d-0dbf-4645-8439-c30602ec7959.png">

Exiting file and saving changes.


### Part 2: VSCode VS Vim

VSCode: 1.32.72 seconds

Vim: 57.16 seconds

No unexpected difficulties came up.

I would prefer using VSCode through, because I think that being able to edit freely without all the extra 'modes' or 'commands' to do so (i.e. using just mouse to go and type)
 is worth the extra time it takes to `scp` over afterwards. Plus, VSCode can catch syntax errors in the editor. Vim, cannot.
 
 Admittedly, Vim took less time in this case, and I would prefer it. But that is only because for this task, I already knew what to do and was familiar with the very short list
  of edits required. It was essentially a 'how fast can I type' game. Had it been a real project where I was required to write code and debug, I would always choose 
  VSCode.
