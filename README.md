# Setting Up AWS Code Commit
---

Generate the key locally..

```
cd $HOME/.ssh
ssh-keygen
[Enter the name test_rsa and leave all fields blank]
cat test_rsa.pub
```
copy the test_rsa.pub content.

---

Now we need to enter our test_rsa.pub content into IAM.

AWS console --> IAM --> Users --> select the appropriate user.
Under Security credentials --> Upload SSH public key

![alt text](https://github.com/taranggupta1987/AWS_Code_Commit/blob/taranggupta1987-images/Screen%20Shot%202018-01-02%20at%206.00.23%20PM.png)

paste the copied content and click the upload button.

---

copy the SSH key ID.

![alt text](https://github.com/taranggupta1987/AWS_Code_Commit/blob/taranggupta1987-images/Screen%20Shot%202018-01-02%20at%206.00.49%20PM.png)

```
nano config

Host git-codecommit.*.amazonaws.com
  User [YOUR_SSH_KEY_ID_GENERATED_USING_IAM]
  IdentityFile ~/.ssh/test_rsa
```

---

Verification time.

```
ssh git-codecommit.us-east-1.amazonaws.com
```

You should see the below message, if connection got success.
---
You have successfully authenticated over SSH. You can use Git to interact with AWS CodeCommit. Interactive shells are not supported.Connection to git-codecommit.us-east-1.amazonaws.com closed by remote host.
Connection to git-codecommit.us-east-1.amazonaws.com closed.
