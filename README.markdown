Modern development is highly asynchronous: isn’t it about time iOS developers had tools that made programming asynchronously powerful, easy and delightful?

```objc
[CLLocationManager promise].catch(^{
    return self.chicagoLocation;
}).then(^(CLLocation *loc){
    return [NSURLConnection GET:@"http://user.net/%f/%f", loc.latitude, loc.longitude];
}).then(^(NSDictionary *user){
    UIAlertView *alert = [UIAlertView new];
    alert.title = [NSString stringWithFormat:@"Hi, %@!", user.name];
    [alert addButtonWithTitle:@"Bye"];
    [alert addButtonWithTitle:@"Hi!"];
    return alert.promise;
}).then(^(NSNumber *tappedButtonIndex){
    if (tappedButtonIndex.intValue == 1) {
        id vc = [HelloViewController new]
        return [self promiseViewController:vc animated:YES completion:nil];
    } else
        return nil;
}).then(^(id resultFromViewController){
    //…
});
```

With PromiseKit, asynchronous development is under control.

PromiseKit is designed to be integrated into the other Pods you use.

PromiseKit is thoroughly documented at [promisekit.org](http://promisekit.org).

PromiseKit is complete, well-tested and in apps in the store.
