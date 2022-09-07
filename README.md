# password-checker
This is a secure way to check if your password has ever been hacked.

It is possible to check whether your account or password were hacked, by opening haveibeenpwned.com in a browser, entering the password you want to check in the browser, and getting a response. It has a dictionary of previously hacked accounts and passwords. While this website is considered secure and doing only what it's supposed to do, you should never really trust a website with your password.

This program makes use of the API provided by haveibeenpwned.com, but it is a much more secure way than putting your whole password in a browser and let it be sent through Internet. Instead, we only trust ourselves, and we're only going to give the bits of information that we feel comfortable to the API, so that it gives us a response with some data that we can then calculate on our own machines that are hypothetically more secure.

I'm using a technique called "K-anonimity", which is used by legitimate (expensive) password managers that keep our password secure.
It allows somebody to receive information about us, yet still not know who we are.

The steps are the following:
- we hash the password using SHA1 algorithm
- we only send to the API the first 5 characters from the hashed string, and retain on our machines the rest of the characters in the hashed string.
- the API will return all the hashes it has in the dictionary of previously hacked passwords, that match the 5 characters that we sent (plus, how many times the passwords have been hacked)
- we calculate on our machine whether the rest of the characters in our hashed password (that we didn't send to the API) match with any of the hashes from API's response.

In order to run the program, first have to instal the requests module from PyPi

```
pip install requests
```

Then, run the program like this (with any number of passwords to check as parameters):

```
python3 main.py your_password1 your_password2 your_password3 
