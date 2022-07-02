# Websites-BestMFA
List of websites with their best 2FA options

## Introduction
## Ranks
Weaker 2FA options override the stronger options, for example, if a website supports hardware token but does not allow SMS OTP to be disabled, it will be ranked lower.

1 - Hardware key only, without any other weaker 2FA options  
2a - Hardware key or backup codes  
2b - Hardware key or e-mail code  
2c - Hardware key or e-mail code or backup codes  
3  - Software TOTP 2FA and e-mail code  
3a - Software TOTP 2FA only  
3b - Software TOTP 2FA or backup codes  
3c - Software TOTP 2FA or e-mail code  
3d - Software TOTP 2FA or e-mail code or backup codes  
4a~4d - 3a~3d but 2FA is skipped 2FA when using certain SSO  
5a - Software TOTP or SMS OTP  
5b - SMS OTP only  

| Website    | Rank  | HW Key | SW TOTP | E-mail | SMS | Backup Code | Notes                                                                              |
|------------|-------|--------|---------|--------|-----|-------------|------------------------------------------------------------------------------------|
| Amazon     | 5a    |        | O       |        | O   |             | No                                                                                 |
| Atlassian  | 4b    |        | O       |        |     | Yes         | 2FA is skipped when using Google, Microsoft, or SAML SSO                           |
| Binance.us | 3     |        | O       | +      |     | No          | E-mail 2FA is required on top of TOTP for new device login                         |
| Bitwarden  | 3b    |        | O       |        |     | Yes         | Non-premium does not support hardware key                                          |
| Discord    | 3b    |        | O       |        |     | Yes         |                                                                                    |
| Docker     | 3b    |        | O       |        |     | Yes         |                                                                                    |
| Facebook   | 1 (?) |        | O       |        |     | Yes         | Message prompt by Facebook indicates possibility to approve login from another logged in device when "Use a different method" is selected during log in |


<!-- You’ve asked us to require a 6-digit login code when anyone tries to access your account from a new device or browser.
When you receive your 6-digit code, enter it to continue:

Approve from another device
Just check your notifications in another browser or phone where you've logged in. -->