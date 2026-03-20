<img width="361" height="291" alt="image" src="https://github.com/user-attachments/assets/544abd97-385f-4b2e-8d8e-523a58c07458" />

# Forensics Git 0
This challenge provides us a disk image and asks if we could find the flag. I started by throwing the image into Autopsy to get a deeper look into what it contains. Since picoCTF flags follow a known format of `picoCTF`, I peformed a keyword search with a substring match in Autopsy and found two results, one named `note.txt` with some information about the flag.
### Keyword Search
<img width="830" height="230" alt="image" src="https://github.com/user-attachments/assets/69140a2f-647a-4704-84fb-7da514fa8a84" />
<img width="618" height="88" alt="image" src="https://github.com/user-attachments/assets/9a0e7667-536e-42b3-bf78-1ac4607fff81" />

The location of the file leads us to the `.git` folder. Going through the repository, under `COMMIT_EDITMSG` where commit messages are stored, I found the text "`Wrap this phrase in the flag format: g17_1n_7h3_d15k_041217d8`." And now we have the flag!
### .git
<img width="817" height="602" alt="image" src="https://github.com/user-attachments/assets/88f34458-48b9-46f8-b07a-f6fefbad83ee" />

### Flag
picoCTF{g17_1n_7h3_d15k_041217d8}
