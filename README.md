# Websites-BestMFA
List of websites with their best MFA options.  
Only for free accounts, does not include Paid/Commercial/Premium service accounts.

## Introduction
One fine day in 2022, bought my security token and its spare, logged in to my favorite website to start securing it. Account Settings, Security and Privacy> WAIT, where is the setting that says, add security token?

Logged in to second website, added security tokens. WAIT, where is the option to remove SMS-2FA??

WAIT! I NEED TO ENROLL IN THIS GOOGLE ADVANCED THREAD PROTECTION to use hardware keys as the only 2FA method? AND I CAN ONLY USE THUNDERBIRD AS E-MAIL CLIENT FROM HERE ONWARDS, AND SYNOLOGY CLOUD WILL STOP WORKING???

Above are the problems you may when trying to use security tokens as your main 2FA method. Since a lot of the websites yet to support security tokens as 2FA I needed to keep a list to remind myself to check them in the future. As I visited more websites, the range of 2FA/MFA options and combinations of them are totally.. unexpectedly unstandardized, and the combinations of different MFA options are as complicated as they can be to consider which would give the best security.

The realization that some websites allow MFA only with SMS-2FA enabled, or give no options to disable less secure 2FA options, and the need to have a standard rule to follow when setting up 2FA/MFA gave birth to this document.

## Ranks
| Rank | Sub-rank | Best 2FA Options                                           | Rank after Removing TOTP & Backup Codes |
|:----:|:--------:|------------------------------------------------------------|:---------------------------------------:|
|  1   |          | Security Tokens only, without any other weaker 2FA options |                No Change                |
|  2   |    a     | Security Tokens, TOTP, Backup Codes                        |                    1                    |
|      |    b     | Security Tokens, E-mail, Backup Codes, Mobile Push         |                   2b                    |
|  3   |    a     | TOTP and E-mail                                            |                No Change                |
|      |    b     | TOTP only                                                  |                No Change                |
|      |    c     | TOTP, Backup Codes                                         |                   3b                    |
|      |    d     | TOTP, E-mail, Backup Codes, Mobile Push                    |                No Change                |
|  4   |   a~e    | 3a~3e but 2FA is skipped when using certain SSO            |                No Change                |
|  5   |    a     | TOTP, SMS-OTP                                              |                No Change                |
|      |    b     | SMS-OTP only                                               |                No Change                |

### Ranks Explaination
1. General security strengths of different 2FA options, in descending order:
    - Security Tokens
    - Hardware-backed TOTP
    - TOTP
    - Backup Codes
    - Mobile Push
    - E-mail
    - SMS

2. Backup codes as secondary 2FA is ranked higher than e-mail as Backup Codes can be deliberately ignored (not saved anywhere when asked during the process of setting up TOTP) to eliminate theft possibility. Since there is a small possibility that user will save this backup code somewhere as instructed when enabling TOTP potentially compromising security, websites that do not support backup code login are ranked higher.

3. For 2a and 2b, TOTP is ranked higher than e-mail code due to several reasons:
   - It can be hardware-backed.
   - E-mail login has more attack surface compare to Software TOTP app.
   - After setup, the TOTP entry can be deliberately removed similar to backup codes.
   - Most of the time the address for e-mail is the same as the account-link e-mail and not possible to be changed/removed. Even if the website supports different address for e-mail code, it can not always be deliberated removed.
   - Though slightly impractical, device that host the TOTP app can be put offline or run on a dedicated phone/PC/sandbox to avoid multi-channel attacks.

4. The difference between Rank 2 and Rank 3 is that for Rank 2, the use security tokens are able to protect against phishing/MitB attack. It should be kept in mind that security tokens shall be used whenever possible, while avoiding the use of other secondary 2FA options. Security is compromised and no better than Rank 3 if users still prefer TOTP over the use of security tokens.

5. E-mail and mobile push are ranked similarly due to both are commonly used on mobile phones, with mobile push ranked slightly higher as e-mail is usually signed on phone, PC browser and desktop client all the time which provide more attack surface.

## Best Practice / General Rule
1. This document mainly focus on website sign in using security tokens.
2. Security tokens must be always used even there are other 2FA options enabled (or irremovable) to maintain upmost security.
3. Hardware-backed TOTP must be always used (e.g. Yubico Authenticator) over normal TOTP (e.g. Authy, Google Authenticator).
4. E-mail, recovery e-mail must be of similar sign-in security level (e.g. an Gmail address enrolled in ATP).
5. Backup codes shall be removed, or stored offline (not on any form of digital device), think of it as a type of single-use security token but without the protection from phishing/MitB.

## Website List
### Table Header Abbreviations
Token - Security Token  
TOTP - Time-based one-time password  
E-Mail - E-mail Code  
SMS - Short Message Service OTP  
B.C. - Backup Codes

| Website     | Rank | Token | TOTP | E-mail | SMS | B.C.     | Notes                                                            |
|-------------|:----:|:-----:|:----:|:------:|:---:|:--------:|------------------------------------------------------------------|
| Amazon      | 5a   |       | O    |        | O   | No       | SMS-2FA required to enable TOTP                                  |
| Atlassian   | 4c   |       | O    |        |     | Yes      | 2FA is skipped when using Google, Microsoft, or SAML SSO         |
| Binance.us  | 3b+  |       | O    | +      |     | No       | E-mail-2FA is required on top of TOTP for new device login       |
| Bitwarden   | 3c   |       | O    |        |     | Yes      | Non-premium does not support security tokens                     |
| Coinbase    | 1    | >1    |      |        |     | No       |                                                                  |
| Discord     | 3c   |       | O    |        |     | Yes      |                                                                  |
| Docker      | 3c   |       | O    |        |     | Yes      |                                                                  |
| Evernote    | 3c   |       | O    |        |     | Yes      | Does not ask for 2FA using Goggle SSO                            |
| Facebook    | 1(?) |       | O    |        |     | Yes      | Message prompt by Facebook indicates possibility to approve login from another logged in device when "Use a different method" is selected.[^fb] To be verified. |
| GitHub      | 2b   | >1    | O    |        |     | Yes      | Force enables GitHub Mobile Push-2FA if mobile app is used       |
| GoodSync    | 3b   |       | O    |        |     | No       |                                                                  |
| Google-ATP  | 1    | >1    |      |        |     | No       | Need to enroll in Advanced Thread Protection                     |
| Google      | 3d   |       | O    |        |     | Optional | Alternative 2FA using Security code from phone, mobile push 2FA  |
| Instagram   | 3c   |       | O    |        |     | Yes      |                                                                  |
| LinkedIn    | 3c   |       | O    |        |     | Yes      |                                                                  |
| LogMeIn     | 3d   |       | O    | O      |     | Yes      |                                                                  |
| Mega        | 2b   | >1    | O    | O      |     | Yes      |                                                                  |
| Microsoft   | 2b   | >1    | O    | O      |     | Yes      | Bypasses username/password prompt when using security token      |
| Parsec      | 3c   |       | O    |        |     | Yes      |                                                                  |
| PayPal      | 1    | 1     |      |        |     | No       | Only supports single security token. Only allows "Primary" 2FA method when set. Removal of recovery phone number is not possible. |
| Reddit      | 3c   |       | O    |        |     | Yes      |                                                                  |
| Synology    | 5a   |       | O    |        | O   | Yes      | SMS-2FA required to enable TOTP                                  |
| TradingView | 3c   |       | O    |        |     | Yes      |                                                                  |
| Twitch      | 5a   |       | O    |        | O   | No       | SMS-2FA required to enable TOTP. Force integrates Authy. [^twc1] |
| Twitter     | 1    | >1    |      |        |     | Yes      |                                                                  |
| Ubisoft     | 5a   |       |      | O      | O   | Yes      | SMS-2FA required to enable E-mail-2FA                            |
| XDA Forums  | 3c   |       | O    |        |     | Yes      |                                                                  |
| Yahoo       | 3c   | >1    |      | O      |     | No       | Requires 2 recovery emails to activate 2FA, but the second e-mail can (shall) be removed after setup. |
| Zoom        | 3c   |       | O    |        |     | Yes      |                                                                  |

[^fb]: "You’ve asked us to require a 6-digit login code when anyone tries to access your account from a new device or browser.
When you receive your 6-digit code, enter it to continue:<br>Approve from another device<br>Just check your notifications in another browser or phone where you've logged in."
[^twc1]: [Authy handles all 2FA for Twitch users. When you enable 2FA on your Twitch account, an Authy account with a unique ID is automatically generated](https://support.authy.com/hc/en-us/articles/360033906974-Twitch-Login-Issues#h_7e0e3895-05d7-4e78-aee0-3fd6a3f15259)

## TODO
- Differentiate Hardware 2FA such as U2F, UAF, FIDO2/WebAuthn
- NiceHash accepts used YubiKey OTP
