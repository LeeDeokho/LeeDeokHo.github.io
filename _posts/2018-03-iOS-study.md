## study-01 
### navigation and singletone

dispatch_once 
는 딱 한번만 호출

보통은 메소드 내부의 static만 쓴다.

2개 필드 변경사항
tag없어지고
platform 계속 들어오고


## study-02
### delegate and GCD

Study-02

protocol 
공통 콜백

protocol delegate는 한 셋트
```swift

@class NEClass;

@protocol NEClassDelegate <NSObject>

- (void) neclass:(NEClass *)neclass 
    value1:(NSString *)value1 
    value2:(NSString *)value2;

@end

@interface NEClass : NSObject

+(instancetype)sharedInstance;

@property (weak, nonatomic) id<NEClassDelegate> dleegate;

- (void) getClass;
- (NSString *) neid;

@end

---

@interface NEClass() {
    @property (string, nonatomic) NSString *nid;
}
@implement NEClass

- (instancetype)init {
    self = [super init];

    if(self) {

        [NSTimeInterval time = [NSDate date] timeIntervalSince1970];
    NSString *timeString = [NSString stringWithFormat:@"%f", time * 1000];
        self.nid = timeString;
    }

    return self;
}

- (NSString *)neid {
    return self.nid;
}

- (void)getClass {

    [NSTimeInterval time = [NSDate date] timeIntervalSince1970];
    NSString *timeString = [NSString stringWithFormat:@"%f", time * 1000];

    NSDateFormatter *format = [[NSDateFormatter alloc] init];
    [format setDateFormat:@"yyyy-MM-dd HH:mm:ss"];
    NSString *date = [format stringFromDate:[NSDate data]];
    
    if(self.delegate != nil && [self.delegate respondsToSelector:@selector(neclass:value1:value2:)])
    [self.delegate neclass:self value1:date value2:timeString];
}

@end




```

```swift

[[NECLass sharedInstance] setDelegate:self];

NEClass *nec = [[NECLass allloc] init];

[nec setDelegate:self];

[nec getClass];



- (void) neclass:(NEClass *)neclass 
    value1:(NSString *)value1 
    value2:(NSString *)value2 {
    // 일반 쓰레드에서 메인 쓰레드 접근하면 크래쉬난다.
    // UI 건드리는 작업은 메인쓰레드에서

    dispatch_async(dispatch_get_main_queue(), ^{
        NSLog(@"%@", neclass.neid);
        NSLog(@"%@", value1);
        NSLog(@"%@", value2);
    });

    dispatch_queue_t queue = dispatch_queue_create("qeueu1", DIAPATCH_QUEUE_PRIORITY_DEFAULT);
    // 관리를 OS에서 다 해준다. 우선순위에 따라서

    dispatch_async(queue, ^{

        @autoreleasepool{
            for(int i = 0; i < 1000; i++) {
                    NSLog(@"[0] %d", i);
                }
        }
        // Thread에서 작업하다 보면 ARC가 제대로 안되는 경우가 있다. 
        // 그럴땐 명시적으로 오토릴리즈풀을 써서 해주자.
    
    })

    
        
    


@interface viewController : UIViewController <NEClassDelegate>

```


두번째 뷰에서 테이블뷰를 만들고 커스텀으로(이미지 사이즈 100이상, ) 1000셀 만들기

셀 눌러서 넘어가면 
이미지, 타이틀, 디스크립션 찍히게

