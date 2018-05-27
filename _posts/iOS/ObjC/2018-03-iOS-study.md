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

## NSDate & NSTimeInterval
NetworkInsight 모듈을 짜면서 NSDate와 NSTimeInterval을 사용했는 데,
NSDate와 NSTimeInterval의 시간이 세컨드 단위인지, 밀리세컨드 단위인지 자세히 알아보지도 않고 사용했다.
개인프로젝트라면 대충 사용해도 되지만, 회사에서 사용할 것이면 자세히 알고써야겠다고 코드리뷰를 하면서 느끼고 이 참에 정리해본다.

### NSTimeInterval
> A number of seconds.
> <br> 초 라고 나와있어서 처음에는 int형이라고 생각했지만, 실제로 사용해보면 "5.02423894405365" 처럼 double형으로 값이 나온다. Declartion을 봐도 double형을 시간에 관계된 것에 쓰게끔 typedef를 해놓은 것이다. 밀리세컨드 이하의 정밀도를 보인다고 나와있는 데, 그것이 정확히 소수점 몇째자리 까지 나오는 지는 문서에는 안나와있다.

> Declartion
>
> typedef double NSTimeInterval;

> Discussion
>
> A NSTimeInterval value is always specified in seconds; it yields sub-millisecond precision over a range of 10,000 years.
---
### NSDate
> A representation of a specific point in time that bridges to Date; use NSDate when you need reference semantics or other Foundation-specific behavior.

> [NSDate date]
>
> Fri Apr 20 21:37:16 2018