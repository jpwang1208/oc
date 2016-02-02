


#简单便捷的网络状态获取方法
#状态栏是由当前app控制的，首先获取当前app
#type数字对应的网络状态依次是 ： 0 - 无网络 ; 1 - 2G ; 2 - 3G ; 3 - 4G ; 5 - WIFI
UIApplication *app = [UIApplication sharedApplication];

NSArray *children = [[[app valueForKeyPath:@"statusBar"] valueForKeyPath:@"foregroundView"] subviews];

int type = 0;
for (id child in children)
{
if ([child isKindOfClass:NSClassFromString(@"UIStatusBarDataNetworkItemView")]) {
type = [[child valueForKeyPath:@"dataNetworkType"] intValue];
}
}
NSLog(@"----%d", type);