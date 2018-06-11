# Terminal  Oath authenticator database

Simple Oath authenticator app that keeps stored your service key and allows to easilly access it.
It keeps the keys salted to  avoid having then in a plain file.

## Dependencies
 - oathtool - The actual oathtool that generates the  one time codes
 - openssl  - used to encrypt and decrypt the data
 - qrencode - used to generate qr codes (https://fukuchi.org/works/qrencode/index.html.en)

## Usage

You can setup the following enviroment variables prior to running the script:
 - `$OATHKEYFILE` - The file where the keys will be stored (defaults to `.oathKeys`)
 - `$GSALT` - you will be asked for a salt keyto encrypt/decrypt your secrets stored in the file. If it is not set, the script will ask everyt time it needs it.


To store a service key

```
$ g.sh -a Facebook "ABCD EFGH IJKL MNOP"
Facebook: 123 456
Storing service key
```


To list stored services codes:
```
$ g.sh -l
Facebook: 123 456
Google: 234 567
```

You can also just filter by a single service
```
$ g.sh -l google
Google: 234 567
```

Print a QR code with the service secret key in your terminal
So it can be added by a qr code
```
$ g.sh -q google
##########################################################################################
##########################################################################################
##########################################################################################
##########################################################################################
########              ##      ##          ########      ##  ##    ##              ########
########  ##########  ##      ####    ##        ########  ##  ##  ##  ##########  ########
########  ##      ##  ##  ##    ####  ##    ####    ##    ######  ##  ##      ##  ########
########  ##      ##  ##    ##  ##        ############            ##  ##      ##  ########
########  ##      ##  ############  ##      ########    ##        ##  ##      ##  ########
########  ##########  ##  ####      ####  ####  ####  ##    ####  ##  ##########  ########
########              ##  ##  ##  ##  ##  ##  ##  ##  ##  ##  ##  ##              ########
##########################  ####  ####        ##    ########    ##########################
########    ####      ########  ######  ######  ##    ################  ##        ########
##############  ######        ##  ##      ########  ##  ##  ##      ####    ##  ##########
##########  ##    ##  ####  ##                ##          ##    ######        ############
########    ####  ######        ####    ##  ##  ##  ##    ######    ########  ############
########    ##    ##    ##    ##  ######    ##  ##    ##  ##  ##      ######      ########
##########      ##  ######  ######  ##    ##  ####  ##  ######    ##  ##  ##    ##########
########  ##  ##        ####  ####  ##        ##  ####    ##    ##  ##  ##    ############
########  ####  ##  ######    ##  ########      ##  ####  ##  ####  ##  ##    ############
####################        ##  ##  ##  ##  ##  ##    ########          ##    ##  ########
##############    ######  ##  ##          ##########    ##      ##  ####  ##  ############
##########  ####  ##              ##    ########          ####  ##########  ##############
##############      ####    ##  ######  ##  ######      ####      ####  ##      ##########
########  ########        ######    ######  ####      ############    ######  ##  ########
########    ##      ##  ##########            ####      ##  ##      ####        ##########
########      ##  ##          ####  ##        ######    ##  ##      ##    ################
########  ####      ##    ######  ####  ##                ##    ####            ##########
################      ######    ##    ##    ##            ######        ####      ########
########      ##  ####  ##    ##  ##          ##        ##        ####          ##########
################  ##                    ##  ####          ##    ##########################
##############  ##  ##  ####    ##  ##  ##    ##      ########    ##########  ##  ########
########                ####  ##    ####    ####          ######                ##########
########################  ##  ####            ########  ##    ##  ######    ##############
########              ####    ########  ####  ######    ##    ##  ##  ##      ############
########  ##########  ##  ######  ##        ##      ############  ######  ##    ##########
########  ##      ##  ##  ####  ##    ####  ####          ######          ##    ##########
########  ##      ##  ####    ##  ######  ##  ######    ##    ####    ####        ########
########  ##      ##  ######                ##########  ##    ##  ##    ##################
########  ##########  ##  ####  ##  ##  ##      ##      ####    ##  ########    ##########
########              ##    ####    ##  ##  ##            ####  ########          ########
##########################################################################################
##########################################################################################
##########################################################################################
```

For more options use the -h flag


### Limitations
- Currently only handling time based secrets (Haven't needed anything else)

### Why?
Why have I done this you would ask? Well, I've became quite dependent on Google authenticator as a two factor authentication so when my mobile started breaking down I came to the scenario where I needed to consider moving my google authenticator keys into another mobile. Not only did that became a boring process as I didn't store the actual keys as my replacement phone keep breaking down (That what happens when you pick old mobiles)

So I decided that having a simple terminal aplication with an identical funcionality as the Google Authenticator  was a must.
Do you need this Tool? Probably not, take in consideration you can use `oathtool`  directly and keep your keys safer.



## License
MIT
