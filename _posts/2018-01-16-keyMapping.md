---
layout: post
title: "2018-01-16-CapsLock-KeyMapping-Tips"
date: 2018-01-16 19:40:06
description: 1월 16일 CapsLock-KeyMapping-Tips
tags: 
 - tips
comments: true
---


# CapsLock을 유용하게 바꾸기
---

## Intro
평소에 잘 사용하지 않는 CapsLock 키를 이용하여 키보드를 최대한 활용하기

--- 

## 기본 사용법
윈도우랑 맥이랑 조금 차이는 있지만 코드 보시면 맵핑이 어떻게 되있는 지 아실
---


## For Windows
AutoHotkey라는 프로그램을 이용해서 키맵핑을 해줍니다.
아래 소스를 받아서 파일명.ahk 로 저장해주시고, 
AutoHotkey를 설치해서 실행프로그램으로 바꾸신 다음에 시작프로그램에 넣어두면 사용하기 편합니다.

```JSON
SetCapsLockState, AlwaysOff		; Disable CapsLock Toggle
$Capslock::Ctrl

!q::send,!{F4}					; Alt+F4 (Close Window)

; 내가 추가하는 부분 시작

CapsLock & Left::send {Home}
CapsLock & Right::send {End}
CapsLock & Down::send {PgDn}
CapsLock & Up::send {PgUp}
PgUp::send {BackSpace}
PgDn::send {Delete}

Shift & PgDn::send,+{Del}
; CapsLock & i:: send,^+z			; CapsLock+I = Ctrl+Shift+Z (ReDo)

CapsLock & j::send,{Left}
CapsLock & k::send,{Down}
CapsLock & l::send,{Right}
CapsLock & i::send,{Up}

CapsLock & u::send,{BackSpace}
CapsLock & o::send,{Del}
CapsLock & p::send,{Browser_Refresh}

; CapsLock & k::send,{Left}
; CapsLock & l::send,{Down}
; CapsLock & `;::send,{Right}
; CapsLock & o::send,{Up}
; CapsLock & i::send,{BackSpace}
; CapsLock & p::send,{Del}
; CapsLock & [::send,{Browser_Refresh}


CapsLock & e::send,{CTRLDOWN}{PgUp}{CTRLUP}
CapsLock & r::send,{CTRLDOWN}{PgDn}{CTRLUP}


CapsLock & a::send,+{Home}
CapsLock & s::send,+{End}
CapsLock & q::send,^+{Home}
CapsLock & w::send,^+{End}
CapsLock & z::send,^{Home}
CapsLock & x::send,^{End}

CapsLock & -::send,^-
CapsLock & =::send,^=


Capslock & /::SetCapsLockState, AlwaysOff
Capslock & <::SetCapsLockState, On
Capslock & >::SetCapsLockState, Off

LAlt & f::run,C:\Program Files\Everything\Everything.exe

#if GetKeyState("CapsLock", "P")
Shift & Left::send,+{Home}
Shift & Right::send,+{End}
Shift & Up::send,^+{Home}
Shift & Down::send,^+{End}
Ctrl & Left::send,^{Home}
Ctrl & Right::send,^{End}

;====================================
Tab & i::send,{PgUp}
Tab & k::send,{PgDn}
Tab & j::send,{Home}
Tab & l::send,{End}

Shift & j::send,+{Left}
Shift & l::send,+{Right}
Shift & i::send,+{Up}
Shift & k::send,+{Right}


;=====================================
; Tab & o::send,{PgUp}
; Tab & l::send,{PgDn}
; Tab & k::send,{Home}
; Tab & `;::send,{End}

; Shift & k::send,+{Left}
; Shift & `;::send,+{Right}
; Shift & o::send,+{Up}
; Shift & l::send,+{Right}

LAlt & Left::send,+#{Left}
LAlt & Right::send,+#{Right}
; LAlt & F::run,C:\Program Files\Everything\Everything.exe
; LAlt & f::MsgBox, Hello World
; MsgBox, Hello World
; CapsLock & 4:: send,^#{Right}
#if


#if GetKeyState("LShift", "P")
LWin & PgUp::send,+#{Left}
LWin & PgDn::send,+#{Right}

#if


; #if GetKeyState("AppsKey", "CapsLock")
; ; CapsLock & Shift & Left::send,+{Home}

; Shift & Left::send,+{Home}
; Shift & Right::send,+{Down}
; Shift & PgUp::send,+{PgUp}
; Shift & PgDn ::send,+{PgDn}

; #if

; Capslock & s::Send, {LEFT}		; CapsLock+S = ←
; Capslock & f::Send, {Right}		; CapsLock+F = →
; Capslock & e::SEnd, {Up}		; CapsLock+E = ↑
; Capslock & d::send,{down} 		; CapsLock+D = ↓
; Capslock & w::Send, {Home}		; CapsLock+W = Home
; Capslock & r::Send,{End}		; CapsLock+R = End
; Capslock & c::send,{delete}	; CapsLock+C = Delete


; Capslock & q::send,{PgUp}		; CapsLock+Q = PageUp
; Capslock & a:: send,{PgDn}		; CapsLock+A = PageDown
; Capslock & z::send,{PgUp}		; CapsLock+Z = PageUp
; Capslock & x:: send,{PgDn}		; CapsLock+X = PageDown
CapsLock & d:: send,{Browser_Back}		; CapsLock+C = Browser Back
CapsLock & f:: send,{Browser_Forward}	; CapsLock+V = Browser Forward
CapsLock & g:: send,{F11}				; CapsLock+G = F11 (InternetBrowser FullScreen)
CapsLock & b:: 							; CapsLock+B = (Alt+E) + B (Open ChromeBrowser's Bookmark)
send, !e ;
send, b ;
return ;
Capslock & t::Send,^t	; CapsLock+T = Ctrl+T (New Teb)

Capslock & y::Send,^w	; CapsLock+Y = Ctrl+W (Close Tab)


CapsLock & 3:: send,#{Tab}		; CapsLock+3 = Win+Tab (View all Virtual Desktops)
CapsLock & 2:: send,^#{Left}	; CapsLock+2 = Crtl+Win+← (Move to Left V.Desktop)<<<<<<<<<
CapsLock & 4:: send,^#{Right}	; CapsLock+4 = Ctrl+Win+→ (Move to Right V.Desktop)
CapsLock & 5:: send,^#d			; CapsLock+5 = Ctrl+Win+D (Create V.Desktop)
CapsLock & 1:: send,^#{F4}		; CapsLock+1 = Ctrl+Win+F4 (Delete V.Desktop)

; Capslock & j:: send,{Media_Prev}		; CapsLock+J = Media_Previous (Play Previous Track)
; Capslock & k:: send,{Media_Play_Pause}	; CapsLock+K = Media_Play_Pause (Play/Pause Track)
; Capslock & l:: send,{Media_Next}		; CapsLock+L = Media_Next (Play Next Track)

CapsLock & m:: send,{AppsKey}	; CapsLock+M = AppsKey (Menu Key)
; CapsLock & u:: send,^z			; CapsLock+U = Ctrl+Z (UnDo)
; CapsLock & i:: send,^+z			; CapsLock+I = Ctrl+Shift+Z (ReDo)
; CapsLock & Shift & Left::send,+{Home}

Capslock & ESC::				; CapsLock+ESC = Screen Blackoutd
;    KeyWait,Ctrl
    PostMessage, 0x112, 0xF170, 2,, Program Manager    
return

```

---


## For Mac

Karabiner라는 프로그램을 이용해서 키맵핑을 해줍니다.
우선 저는 CapsLock 키를 Fn 키로 바꾸고 
한영 전환은 left_control + spacebar인데, 잘 안쓰는 right_command로 사용하고 있습니다.

```JSON
{
    "global": {
        "check_for_updates_on_startup": true,
        "show_in_menu_bar": true,
        "show_profile_name_in_menu_bar": false
    },
    "profiles": [
        {
            "complex_modifications": {
                "parameters": {
                    "basic.to_delayed_action_delay_milliseconds": 500,
                    "basic.to_if_alone_timeout_milliseconds": 1000
                },
                "rules": [
                    {
                        "description": "Change fn + I/J/K/L to Arrow Keys",
                        "manipulators": [
                            {
                                "from": {
                                    "key_code": "i",
                                    "modifiers": {
                                        "mandatory": [
                                            "fn"
                                        ],
                                        "optional": [
                                            "any"
                                        ]
                                    }
                                },
                                "to": [
                                    {
                                        "key_code": "up_arrow"
                                    }
                                ],
                                "type": "basic"
                            },
                            {
                                "from": {
                                    "key_code": "j",
                                    "modifiers": {
                                        "mandatory": [
                                            "fn"
                                        ],
                                        "optional": [
                                            "any"
                                        ]
                                    }
                                },
                                "to": [
                                    {
                                        "key_code": "left_arrow"
                                    }
                                ],
                                "type": "basic"
                            },
                            {
                                "from": {
                                    "key_code": "k",
                                    "modifiers": {
                                        "mandatory": [
                                            "fn"
                                        ],
                                        "optional": [
                                            "any"
                                        ]
                                    }
                                },
                                "to": [
                                    {
                                        "key_code": "down_arrow"
                                    }
                                ],
                                "type": "basic"
                            },
                            {
                                "from": {
                                    "key_code": "l",
                                    "modifiers": {
                                        "mandatory": [
                                            "fn"
                                        ],
                                        "optional": [
                                            "any"
                                        ]
                                    }
                                },
                                "to": [
                                    {
                                        "key_code": "right_arrow"
                                    }
                                ],
                                "type": "basic"
                            }
                        ]
                    }
                    ,
                    {
                        "description": "My Settings",
                        "manipulators": [
                            {
                                "from": {
                                    "key_code": "right_command",
                                    "modifiers": {
                                        "optional": [
                                            "any"
                                        ]
                                    }
                                },
                                "to": [
                                    {
                                        "key_code": "spacebar",
                                        "modifiers": [
                                            "left_control"
                                        ]
                                    }
                                ],
                                "type": "basic"
                            },
                            {
                                "from": {
                                    "key_code": "e",
                                    "modifiers": {
                                        "mandatory": [
                                            "fn"
                                        ],
                                        "optional": [
                                            "any"
                                        ]
                                    }
                                },
                                "to": [
                                    {
                                        "key_code": "left_arrow",
                                        "modifiers": [
                                            "left_option",
                                            "left_command"
                                        ]
                                    }
                                ],
                                "type": "basic"
                            },
                             {
                                "from": {
                                    "key_code": "r",
                                    "modifiers": {
                                        "mandatory": [
                                            "fn"
                                        ],
                                        "optional": [
                                            "any"
                                        ]
                                    }
                                },
                                "to": [
                                    {
                                        "key_code": "right_arrow",
                                        "modifiers": [
                                            "left_option",
                                            "left_command"
                                        ]
                                    }
                                ],
                                "type": "basic"
                            },
                            {
                                "from": {
                                    "key_code": "t",
                                    "modifiers": {
                                        "mandatory": [
                                            "fn"
                                        ],
                                        "optional": [
                                            "any"
                                        ]
                                    }
                                },
                                "to": [
                                    {
                                        "key_code": "t",
                                        "modifiers": [
                                            "left_command"
                                        ]
                                    }
                                ],
                                "type": "basic"
                            },
                             {
                                "from": {
                                    "key_code": "d",
                                    "modifiers": {
                                        "mandatory": [
                                            "fn"
                                        ],
                                        "optional": [
                                            "any"
                                        ]
                                    }
                                },
                                "to": [
                                    {
                                        "key_code": "left_arrow",
                                        "modifiers": [
                                            "left_command"
                                        ]
                                    }
                                ],
                                "type": "basic"
                            },
                            {
                                "from": {
                                    "key_code": "f",
                                    "modifiers": {
                                        "mandatory": [
                                            "fn"
                                        ],
                                        "optional": [
                                            "any"
                                        ]
                                    }
                                },
                                "to": [
                                    {
                                        "key_code": "right_arrow",
                                        "modifiers": [
                                            "left_command"
                                        ]
                                    }
                                ],
                                "type": "basic"
                            }
                        ]
                    }

                ]
            },
            "devices": [],
            "fn_function_keys": [
                {
                    "from": {
                        "key_code": "f1"
                    },
                    "to": {
                        "consumer_key_code": "display_brightness_decrement"
                    }
                },
                {
                    "from": {
                        "key_code": "f2"
                    },
                    "to": {
                        "consumer_key_code": "display_brightness_increment"
                    }
                },
                {
                    "from": {
                        "key_code": "f3"
                    },
                    "to": {
                        "key_code": "mission_control"
                    }
                },
                {
                    "from": {
                        "key_code": "f4"
                    },
                    "to": {
                        "key_code": "launchpad"
                    }
                },
                {
                    "from": {
                        "key_code": "f5"
                    },
                    "to": {
                        "key_code": "illumination_decrement"
                    }
                },
                {
                    "from": {
                        "key_code": "f6"
                    },
                    "to": {
                        "key_code": "illumination_increment"
                    }
                },
                {
                    "from": {
                        "key_code": "f7"
                    },
                    "to": {
                        "consumer_key_code": "rewind"
                    }
                },
                {
                    "from": {
                        "key_code": "f8"
                    },
                    "to": {
                        "consumer_key_code": "play_or_pause"
                    }
                },
                {
                    "from": {
                        "key_code": "f9"
                    },
                    "to": {
                        "consumer_key_code": "fastforward"
                    }
                },
                {
                    "from": {
                        "key_code": "f10"
                    },
                    "to": {
                        "consumer_key_code": "mute"
                    }
                },
                {
                    "from": {
                        "key_code": "f11"
                    },
                    "to": {
                        "consumer_key_code": "volume_decrement"
                    }
                },
                {
                    "from": {
                        "key_code": "f12"
                    },
                    "to": {
                        "consumer_key_code": "volume_increment"
                    }
                }
            ],
            "name": "Default profile",
            "selected": true,
            "simple_modifications": [
                {
                    "from": {
                        "key_code": "caps_lock"
                    },
                    "to": {
                        "key_code": "fn"
                    }
                }
            ],
            "virtual_hid_keyboard": {
                "caps_lock_delay_milliseconds": 0,
                "keyboard_type": "ansi"
            }
        }
    ]
}


```