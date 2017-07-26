---
title: auth.signUp
description: auth.signUp parameters, return type and example
---
## Method: auth.signUp  
[Back to methods index](index.md)


*You cannot use this method directly, use the complete_signup method instead (see https://daniil.it/MadelineProto for more info)*




### Parameters:

| Name     |    Type       | Required |
|----------|:-------------:|---------:|
|phone\_number|[string](../types/string.md) | Yes|
|phone\_code\_hash|[string](../types/string.md) | Yes|
|phone\_code|[string](../types/string.md) | Yes|
|first\_name|[string](../types/string.md) | Yes|
|last\_name|[string](../types/string.md) | Yes|


### Return type: [auth\_Authorization](../types/auth_Authorization.md)

### Example:


```
$MadelineProto = new \danog\MadelineProto\API();
if (isset($token)) { // Login as a bot
    $MadelineProto->bot_login($token);
}
if (isset($number)) { // Login as a user
    $sentCode = $MadelineProto->phone_login($number);
    echo 'Enter the code you received: ';
    $code = '';
    for ($x = 0; $x < $sentCode['type']['length']; $x++) {
        $code .= fgetc(STDIN);
    }
    $MadelineProto->complete_phone_login($code);
}

$auth_Authorization = $MadelineProto->auth->signUp(['phone_number' => 'string', 'phone_code_hash' => 'string', 'phone_code' => 'string', 'first_name' => 'string', 'last_name' => 'string', ]);
```

Or, if you're using the [PWRTelegram HTTP API](https://pwrtelegram.xyz):

### As a bot:

POST/GET to `https://api.pwrtelegram.xyz/botTOKEN/madeline`

Parameters:

* method - auth.signUp
* params - `{"phone_number": "string", "phone_code_hash": "string", "phone_code": "string", "first_name": "string", "last_name": "string", }`



### As a user:

POST/GET to `https://api.pwrtelegram.xyz/userTOKEN/auth.signUp`

Parameters:

phone_number - Json encoded string
phone_code_hash - Json encoded string
phone_code - Json encoded string
first_name - Json encoded string
last_name - Json encoded string



Or, if you're into Lua:

```
auth_Authorization = auth.signUp({phone_number='string', phone_code_hash='string', phone_code='string', first_name='string', last_name='string', })
```
