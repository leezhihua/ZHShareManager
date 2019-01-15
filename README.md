# ZHShareManager
分享集成，自定义分享，锚点分享
>自定义分享
```
NSMutableArray *allMenus = [NSMutableArray arrayWithCapacity:0];
NSArray *types = @[@(SharePlatformTypeWxTimeLine),
                   @(SharePlatformTypeWxSession),
                   @(SharePlatformTypeQQ),
                   @(SharePlatformTypeQzone),
                   @(SharePlatformTypeEmail)];
NSArray *titles = @[@"朋友圈",@"微信好友",@"QQ",@"QQ空间",@"链接"];
NSArray *imageNames = @[@"share－Circle of Friends",@"share－WeChat",@"share－QQ Friends",@"share－QQ Space",@"share-Password"];
[types enumerateObjectsUsingBlock:^(NSNumber *obj, NSUInteger idx, BOOL * _Nonnull stop) {
    ZHShareMenu *menu = [[ZHShareMenu alloc] init];
    menu.title = titles[idx];
    menu.imageName = imageNames[idx];
    ZHShareObject *object = [[ZHShareObject alloc] init];
    object.platformType = obj.integerValue;
    object.objectType = ShareObjectTypeURL;
    object.title = @"分享";
    object.url = @"https://www.apple.com";
    object.thumImage = [UIImage imageNamed:@"share-Password replication"];
    menu.shareObject = object;
    [allMenus addObject:menu];
}];
[ZHShareManager configShareMenus:allMenus.copy];
if (sender.tag == 10000) {
    [[ZHShareManager sharedManager] showCustomActionSheetShareMenuOnSelectPlatform:^(SharePlatformType platformType, NSDictionary *userInfo) {
        
    } completion:^(id result, NSError *error) {
        
    }];
} else if (sender.tag == 20000){ //锚点分享
    [[ZHShareManager sharedManager] showCustomAnchorShareMenuWithAnchorView:sender onSelectPlatform:^(SharePlatformType platformType, NSDictionary *userInfo) {
        
    } completion:^(id result, NSError *error) {
        
    }];
} else {
    CGPoint pt = CGPointMake(sender.center.x, CGRectGetMaxY(sender.frame));
    [[ZHShareManager sharedManager] showCustomAnchorShareMenuWithAnchor:pt onSelectPlatform:^(SharePlatformType platformType, NSDictionary *userInfo) {
        
    } completion:^(id result, NSError *error) {
        
    }];
}
```
