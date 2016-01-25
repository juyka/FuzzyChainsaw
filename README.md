# FuzzyChainsaw
Objective-C streams implementation.

```Objective-C
BMStream *loginStream;
BMStream *passwordStream;

passwordStream
    .filter(^(NSString *password) {
        return password.length > 6;
    })
    .map(^(NSString *password) {
        return md5(password);
    });

loginStream
    .combineLatestWith(passwordStream)
    .reduce(^(NSString *login, NSString *password) {
        return @(login.length && password.length);
    });
```
