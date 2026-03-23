<img width="361" height="282" alt="image" src="https://github.com/user-attachments/assets/3c9a8c40-2349-4006-882d-b3f269be38e9" />

# Forensics Git 1
This challenge is very similar to "Forensics Git 0," but it builds more into the challenge. It provides us with a disk image and asks if we could find the flag. I started by throwing this image into Autopsy to get a deeper look into the disk. Following the same steps as the previous challenge, I did a keyword search for `picoCTF` with a substring match. However, this time I got no results, interesting.
### No Results
<img width="291" height="166" alt="image" src="https://github.com/user-attachments/assets/490dec30-4340-4a3e-bed3-c3040572b1d0" />

Since we know the challenge is going to have something to do with a git repository, I located it using the same location identified in the last challenge and started my search.
### Git Location
<img width="985" height="493" alt="image" src="https://github.com/user-attachments/assets/0190d545-eb32-4c49-bf12-00e63436c8f0" />

There were no obvious flags in plain view. However, under the `COMMIT_EDITMSG` file, there is a commit message that states "Remove flag." This tells us that the flag is no longer in this recent commit, and we would have to read an older commit in order to get the flag. 
### Commit Message
<img width="409" height="133" alt="image" src="https://github.com/user-attachments/assets/7c24b890-5a77-4ca0-8ec5-f869ae41246f" />

First, I extracted the .git repository from Autopsy to my Linux machine where I can do deeper analysis outside of Autopsy. There are many useful commands you can use with `git`. To read more about them, use `git --help`. Once inside the repository on my Linux machine, I used `git log` to show all the commit logs.
### Git Log
<img width="536" height="250" alt="image" src="https://github.com/user-attachments/assets/d40861f2-26e0-469e-a059-3764d74367cd" />

We can see the commit message we saw in Autopsy "Remove flag," but now we can see "Add flag" along with the commit hash. Since Git preserves historical states, the commit hash associated with 'Add flag' can be used to recover the file contents prior to its removal. Using the commit hash associated with the "Add flag" message, I ran: `git show 177789af0b300e043ea8f54ea57d6cee352291ae` to display that commit with the flag.
### Git Show
<img width="507" height="310" alt="image" src="https://github.com/user-attachments/assets/890ab5a9-57ea-4cb6-ab41-bfb5f3a95a8c" />

Success! We now have the flag!

### Flag
**picoCTF{g17_r3m3mb3r5_d4ddf904}**

Challenges could make you feel like you hit a dead end, but sometimes you need to think outside the box. In this case, the flag wasn't within Autopsy and it took deeper analysis outside of it with different tools.
