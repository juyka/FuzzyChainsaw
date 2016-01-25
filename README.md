# FuzzyChainsaw
Objective-C streams implementation.

```Objective-C
BMStream *loginStream;
BMStream *passwordStream;

passwordStream
    .map(^(NSString *password) {
        return password.md5;
    });

loginStream
    .combineLatestWith(passwordStream)
    .reduce(^(NSString *login, NSString *password) {
        return @(login.length && password.length);
    });
```
