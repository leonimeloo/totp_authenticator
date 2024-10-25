# TOTP Authenticator

A Dart package to generate and verify Time-based One-Time Passwords (TOTP) that works with authenticator apps like Google Authenticator, Microsoft Authenticator, and more.

## Features

- 🔑 **Create Secret Key**: Generates a secret key to be used for TOTP generation.
- ✔️ **Verify TOTP Code**: Verifies the code input by the user against the generated code.
- 🚀 **Generate TOTP Code**: Generates the TOTP code based on the secret key and current time.
- 📸 **Get QR Code or URI to Scan**: Generates a URI or QR code for apps like Google Authenticator or Microsoft Authenticator to scan.

## Tested Authenticator Apps

| Logo                                    | Service Name            | Status       |
|-----------------------------------------|-------------------------|--------------|
| <img width="40" src="https://play-lh.googleusercontent.com/NntMALIH4odanPPYSqUOXsX8zy_giiK2olJiqkcxwFIOOspVrhMi9Miv6LYdRnKIg-3R=w480-h960-rw"/> | Google Authenticator    | ✅ Supported |
| <img width="40" src="https://play-lh.googleusercontent.com/_1CV99jklLbXuun-6E7eCPR-sKKeZc602rhw_QHZz-qm7xrPdgWsJVc7NtFkkliI8No=w480-h960-rw"/> | Microsoft Authenticator | ✅ Supported |

## Usage

### `generateSecret()`
   - Generates a random secret key in Base32 format. The secret key is used to generate the TOTP codes that will be verified by authenticator apps.
   
   **Example**:
   ```dart
   String secretKey = TOTP.generateSecret();
   print(secretKey);
   ```

### `generateTOTPCode(String secretKey, {int interval = 30})`
   - Generates a TOTP (Time-based One-Time Password) code based on the provided secret key and the current time. The code changes every X seconds, where X is defined by the interval.
   - **Parameters**:
        - secretKey (required): The Base32-encoded secret key that was generated previously.
        - interval (optional, default: 30): The time interval (in seconds) for which each code is valid. Default is 30 seconds.
   
   **Example**:
   ```dart
   String otpCode = totp.generateTOTPCode(secretKey);
   print('Generated TOTP code: $otpCode');
   ```

### `verifyCode(String secretKey, String otpCode, {int interval = 30})`
   - Generates a TOTP (Time-based One-Time Password) code based on the provided secret key and the current time. The code changes every X seconds, where X is defined by the interval.
   - **Parameters**:
        - secretKey (required): The Base32-encoded secret key that was generated previously.
        - otpCode (required): The user-provided TOTP code that you want to verify.
        - interval (optional, default: 30): The time interval (in seconds) for which each code is valid. Default is 30 seconds.
   
   **Example**:
   ```dart
   bool isValid = totp.verifyCode(secretKey, otpCode);
   print(isValid ? 'Valid code' : 'Invalid code');
   ```

### `generateQRCodeUri(String appName, String secretKey, {String issuer = 'totp_authenticator', int interval = 30})`
   - Generates a URI that can be used by TOTP-based authenticator apps to scan and set up an account for the user. This URI can be used to create a QR code.
   
   **Example**:
   ```dart
   String uri = totp.generateQRCodeUri('MyApp', secretKey);
   print('URI for QR Code: $uri');
   ```

### `generateQRCodeUrl(String appName, String secretKey, {String issuer = 'totp_authenticator'})`
   - Same as generateQRCodeUri(), but it returns qr code direct url.
   
   **Example**:
   ```dart
   String qrCodeUrl = totp.generateQRCodeUrl('MyApp', secretKey);
   print('QR Code URL: $qrCodeUrl');
   
   //Image.Network(qrCodeUrl);
   ```

## License

- This project is licensed under the MIT License. See the LICENSE file for details.

## Issues or Pull requests

### Report Issues

Please report any issues or bugs to our [GitHub repository](https://github.com/leonimeloo/totp_authenticator).

###### © 2024 Leoni Melo, Licensed under MIT