---
Title: Users 
Author: Udensi Fortune Arua
Date: 18-08-2023
---
# Users

## Step one (create a user)
- I first created a Linux environment in my bash terminal using the command `vagrant ssh`
![vagrant ssh](<Screenshot 2023-08-18 105618.png>)

- I created a user named `Udensi`. I also wrote a command to check that the user was successfuly created. I used the following commands to achieve this:
`sudo user add Udensi` and `id Udensi` respectively.
![User1: Udensi](<Screenshot 2023-08-18 135615.png>)

## Step two(set an expiry date of 2 weeks for the user)
- I used the command `sudo usermod --expiredate 2023-09-01 Udensi` to enable expiration of Udensi's account in the next two weeks. 
  
- To ensure the expiry date was set for the user, I used the command `sudo chage -l Udensi` to check the expiry details.
 ![Expiry date](<Screenshot 2023-08-18 112106.png>) 

 ## Step three(prompt the user to change their password on login)
 I used this command to enable this prompt: `sudo chage -d 0 Udensi`
 ![change password](<Screenshot 2023-08-18 112509.png>)

 ## Step four(attach the user to a group called AltSchool)
- I first created a group called "AltSchool" with this command:
`sudo groupadd AltSchool`

- Secondly, I crosscheked to ensure the group was added. I used this command: `getent group AltSchool`

- To attach Udensi to AltSchool, I used the command `sudo usermod -aG AltSchool Udensi`

- Lastly, I did a check to ensure Udensi was added to the AltSchool group,I used this code: `groups Udensi`
![AltSchool group](<Screenshot 2023-08-18 113054.png>)  
![Attached Udensi to AltSchool group](<Screenshot 2023-08-18 113634.png>)

## Step five(allow AltSchool group to be able to run only cat command on /etc/)
To achieve this step, I used the command `echo "%AltSchool ALL=(ALL) /bin/cat /etc/*" | sudo tee /etc/sudoers.d/Altschool_cat`
![cat command](<Screenshot 2023-08-18 154201.png>)

The command adds a sudoers configuration that allows members of the AltSchool group to run the cat command on /etc/.

## Step six(create another user. Make sure that this user doesn't have a home directory)
- I used the following command to create a new user(Fortune) and to ensure that the user doesn't have a home directory: `sudo -M Fortune`
  
- I also did a check to ensure the user was added. I used this command: `id Fortune`
![User2:Fortune](<Screenshot 2023-08-18 114621.png>)





