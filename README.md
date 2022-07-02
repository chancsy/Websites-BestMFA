# Websites-BestMFA
List of websites with their best 2FA options

## Introduction
## Ranks
Weaker 2FA options override the stronger options, for example, if a website supports hardware token but does not allow SMS OTP to be disabled, it will be ranked lower.

| Rank | Sub-rank | Best 2FA Options                                        |
|:----:|:--------:|---------------------------------------------------------|
|  1   |          | Hardware key only, without any other weaker 2FA options |
|  2   |    a     | Hardware key or backup codes                            |
|      |    b     | Hardware key or e-mail code                             |
|      |    c     | Hardware key or e-mail code or backup codes             |
|  3   |          | Software TOTP 2FA and e-mail code                       |
|      |    a     | Software TOTP 2FA only                                  |
|      |    b     | Software TOTP 2FA or backup codes                       |
|      |    c     | Software TOTP 2FA or e-mail code                        |
|      |    d     | Software TOTP 2FA or e-mail code or backup codes        |
|  4   |   a~d    | 3a~3d but 2FA is skipped 2FA when using certain SSO     |
|  5   |    a     | Software TOTP or SMS OTP                                |
|      |    b     | SMS OTP only                                            |

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