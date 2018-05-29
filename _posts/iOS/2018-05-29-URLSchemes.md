---
layout: post
title: "URL Schemes이란?"
date: 2018-05-29 14:30:06
description: URL Schemes에 대해 정리
tags: 
 - ios
comments: true
---

# iOS에서 앱 끼리의 통신

* 앱 끼리의 통신에는 AirDrop을 사용하는 방식과 URL Schemes를 사용하는 방식이 있다. AirDrop은 당장 사용할 필요가 없어서 우선 URL Schemes를 이용한 방식을 알아본다.

# URL Schemes
* URL Schemes을 이용하면 정의한 프로토콜을 통해 다른 앱과 통신 할 수 있다.
* 이러한 체계를 구현하는 앱과 통신하려면 알맞은 형식의 URL을 만들고 시스템에 열어달라고 요청해야한다.

# Sending a URL to Another App

* custom URL scheme을 구현하는 앱에 데이터를 보내려면 적절하게 형식이 지정된 URL을 만들고 앱 객체의 `openURL:` 메소들르 호출하면 된다. <br>
`openURL:` 메소드는 등록된 체계로 앱을 시작하고 URL을 전달한다. 이 시점에서 컨트롤은 새 앱으로 넘어간다. 

* 앱이 custom URL scheme을 정의하는 경우 custom URL scheme 구현에 설명 된대로 해당 스키마에 대한 핸들러를 구현해야한다. URL형식을 지정하는 방법을 비롯하여 시스템 지원 URL 체계에 대한 자세한 내용은 [Apple URL Scheme Reference](https://developer.apple.com/library/content/featuredarticles/iPhoneURLScheme_Reference/Introduction/Introduction.html#//apple_ref/doc/uid/TP40007899)
를 참조

>OBJECTIVE-C
{:.filename}
{% highlight swift %}

NSURL *myURL = [NSURL URLWithString:@"todolist://www.acme.com?Quarterly%20Report#200806231300"];
[[UIApplication sharedApplication] openURL:myURL];

{% endhighlight %}

# Implementing Custom URL Schemes

* 앱이 특별히 형식이 지정된 URL을 수신할 수 있는 경우 해당 URL schemes를 시스템에 등록해야한다. 앱은 종종 custom URL schemes를 사용하여 다른 앱에 서비스를 제공한다. 예로, 지도 앱은 특정 지도 위치를 표시하기위한 URL을 지원한다.

# Registering Custom URL Schemes
* 앱의 URL 유형을 등록하려면 앱의 `Info.plist` 파일에 `CFBundleURLTypes` 키를 포함시킨다. `CFBundleURLTypes` 키에는 dictionary array가 포함되어 있다. 각 dictionary는 앱에서 지원하는 URL scheme를 정의한다. 

> Note: 둘 이상의 third-party app(타사 앱)이 동일한 URL scheme를 처리하도록 등록한 경우, 현재 해당 스키마에 제공할 앱을 결정하는 프로세스가 없다.

# Handling URL Requests
* 자체 custom URL scheme가 있는 앱은 전달된 URL을 처리할 수 있어야한다.
모든 URL은 실행시 또는 앱 실행 중 또는 백그라운드에서 app delegate에게 전달된다. 
들어오는 URL을 처리하려면, delegate가 다음의 메소드를 구현해야한다. 

    * [application:willFinishLaunchingWithOptions:](https://developer.apple.com/documentation/uikit/uiapplicationdelegate/1623032-application?language=objc)와 [application:didFinishLaunchingWithOptions:](https://developer.apple.com/documentation/uikit/uiapplicationdelegate/1622921-application?language=objc) 메소드는 URL에 대한 정보를 검색하고 URL 열기 여부를 결정하는 메소드이다. 두 메소드 중 하나가 `NO`를 반환하면 앱의 URL 처리 코드가 호출되지 않는다.

    * [application:openURL:sourceApplication:annotation:](https://developer.apple.com/documentation/uikit/uiapplicationdelegate/1623073-application?language=objc) 메서드를 사용하여 파일을 연다.

* URL 요청이 도착했을 때 앱이 실행 중이 아니면 앱이 시작되고 URL을 열 수 있도록 foreground로 이동한다. application:willFinishLaunchingWithOptions: 이나 application:didFinishLaunchingWithOptions:
메소드의 구현은 options dictionary에서 URL을 검색하고 앱이 URL을 열 수 있는 지 여부를 결정해야한다. 가능한 경우 YES를 반환하고, app에 openURL:sourceApplication :annotation : (또는 appication:handleOpenURL)메서드를 사용하여 실제 URL 열기를 처리하도록한다. 두 가지 방법을 모두 구현하는 경우 URL을 열기 전에 둘 다 YES를 반환해야한다.

![img]({{ '/assets/images/iOS/URLSchemes/URLSchemeFlow.png' | relative_url }}){: .center-image }

* URL 요청이 도착하면 앱이 실행중이지만 background에 있거나 일시중지된 경우 URL이 열리기 위해 foreground로 이동된다. 잠시 후 시스템은 delegate의 application:openURL:sourceApplication:annotation: 메서드를 URL을 확인하고 열기위해 호출한다. 아래 그림은 app을 foreground로 이동하여 URL을 여는 프로세스를 보여준다. 

![img]({{ '/assets/images/iOS/URLSchemes/URLSchemeFlow2.png' | relative_url }}){: .center-image }

> Note: custom URL schemes을 지원하는 app은 URL을 처리하기 위해 app을 실행할 때 표시할 다른 시작이미지를 지정할 수 있다. 이러한 시작 이미지를 지정하는 방법에 대한 자세한 내용은 [Displaying a Custom Launch Image When a URL is Opened
](#Displaying-a-Custom-Launch-Image-When-a-URL-is-Opened)에 나와있다.


**Handling a URL request based on a custom scheme**

>OBJECTIVE-C
{:.filename}
{% highlight swift %}
- (BOOL)application:(UIApplication *)application openURL:(NSURL *)url
        sourceApplication:(NSString *)sourceApplication annotation:(id)annotation {
    if ([[url scheme] isEqualToString:@"todolist"]) {
        ToDoItem *item = [[ToDoItem alloc] init];
        NSString *taskName = [url query];
        if (!taskName || ![self isValidTaskString:taskName]) { // must have a task name
            return NO;
        }
        taskName = [taskName stringByReplacingPercentEscapesUsingEncoding:NSUTF8StringEncoding];
 
        item.toDoTask = taskName;
        NSString *dateString = [url fragment];
        if (!dateString || [dateString isEqualToString:@"today"]) {
            item.dateDue = [NSDate date];
        } else {
            if (![self isValidDateString:dateString]) {
                return NO;
            }
            // format: yyyymmddhhmm (24-hour clock)
            NSString *curStr = [dateString substringWithRange:NSMakeRange(0, 4)];
            NSInteger yeardigit = [curStr integerValue];
            curStr = [dateString substringWithRange:NSMakeRange(4, 2)];
            NSInteger monthdigit = [curStr integerValue];
            curStr = [dateString substringWithRange:NSMakeRange(6, 2)];
            NSInteger daydigit = [curStr integerValue];
            curStr = [dateString substringWithRange:NSMakeRange(8, 2)];
            NSInteger hourdigit = [curStr integerValue];
            curStr = [dateString substringWithRange:NSMakeRange(10, 2)];
            NSInteger minutedigit = [curStr integerValue];
 
            NSDateComponents *dateComps = [[NSDateComponents alloc] init];
            [dateComps setYear:yeardigit];
            [dateComps setMonth:monthdigit];
            [dateComps setDay:daydigit];
            [dateComps setHour:hourdigit];
            [dateComps setMinute:minutedigit];
            NSCalendar *calendar = [s[NSCalendar alloc] initWithCalendarIdentifier:NSGregorianCalendar];
            NSDate *itemDate = [calendar dateFromComponents:dateComps];
            if (!itemDate) {
                return NO;
            }
            item.dateDue = itemDate;
        }
 
        [(NSMutableArray *)self.list addObject:item];
        return YES;
    }
    return NO;
}
{% endhighlight %}


# Displaying a Custom Launch Image When a URL is Opened

* custom URL schemes를 지원하는 앱은 각 scheme에 custom 시작 이미지를 설정할 수 있다.
시스템이 URL을 처리하기 위해 앱을 실행하고 관련 스냅 샷을 사용할 수없는 경우 지정한 시작 이미지를 표시한다. 시작 이미지를 지정하려면 다음 이름 지정 규칙을 사용하는 이름의 PNG 이미지를 제공해야한다.
    * `<basename>-<url_scheme><other_modifiers>.png`

* 위의 명명규칙에서 basename은 앱의 info.plist 파일에 있는 UILaunchImageFile 키로 지정된 기본 이미지 이름을 나타낸다. 사용자 정의 기본 이름을 지정하지 않으면 기본값인 문자열을 사용하여야한다. 이름의 <url_scheme> 부분은 URL 스키마 이름이다. myapp URL 체계에 대한 일반 시작 이미지를 지정하려면 app bundle에 Default-myapp@2x.png라는 이름의 이미지 파일을 포함시켜야한다. (@ 2x 수정자는 이미지가 망막 디스플레이를 위한 것임을 나타내며, 앱이 표준 해상도 디스플레이도 지원하는 경우 Default-myapp.png 이미지도 제공한다.)

* 시작 이미지 이름에 포함 할 수있는 다른 수정자에 대한 정보는 (Information Property List Key Reference)[https://developer.apple.com/library/content/documentation/General/Reference/InfoPlistKeyReference/Introduction/Introduction.html#//apple_ref/doc/uid/TP40009247] 에서 `UILaunchImageFile` name key에 대한 설명을 참조.



# 참조
[애플 가이드](https://developer.apple.com/library/content/documentation/iPhone/Conceptual/iPhoneOSProgrammingGuide/Inter-AppCommunication/Inter-AppCommunication.html)


