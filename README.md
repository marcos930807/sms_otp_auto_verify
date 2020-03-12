# sms_otp_auto_verify

A new Flutter plugin to provide SMS auto fill and Textfield for OTP Code.
for auto fill, it's only work in android.


<img width="220px" alt="Example App " src="https://raw.githubusercontent.com/oohyugi/sms_auto_verify/master/screenshots/img.jpg"/>

## Getting Started
Import package
```dart
import 'package:sms_otp_auto_verify/sms_otp_auto_verify.dart';
```
Get Signature Code
```dart
  String signature = await SmsRetrieved.getAppSignature();
```
### Add Widget
codeLength must equals with your Sms OTP length

```dart
OtpListTextField(
                  filled: true,
                  filledColor: Colors.grey[100],
                  codeLength: _otpCodeLength,
                  boxSize: 48,
                  onOtpCallback: (code, isAutofill) =>
                      _onOtpCallBack(code, isAutofill),
                )
```

Listen result from OtpListTextField
```dart
_onOtpCallBack(String otpCode, bool isAutofill) {
    setState(() {
      this._otpCode = otpCode;
      if (otpCode.length == _otpCodeLength && isAutofill) {
        _enableButton = false;
        _isLoadingButton = true;
        _verifyOtpCode();
      } else if (otpCode.length == _otpCodeLength && !isAutofill) {
        _enableButton = true;
        _isLoadingButton = false;
      }else{
        _enableButton = false;
      }
    });
  }
```

Example Sms
```html
<#> ExampleApp: Your code is 123456
   r64Iw/6mD1D
```


