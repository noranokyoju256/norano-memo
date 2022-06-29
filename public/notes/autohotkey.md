---
aliases: ['AutoHotkey']
tags: []
datetime-created: '2022-06-29 14:54'
---

# AutoHotkey
- [公式サイト](https://www.autohotkey.com/)
- [非公式日本語Wiki](http://ahkwiki.net/Top)
- AutoHotkeyの基本的なことが大体わかる素晴らしい記事
	- [【AutoHotkey】キーに別の機能（キー）を割り当てるソフトの使い方](https://www.naporitansushi.com/autohotkey/)
## 私が使ってるスクリプト（マジで汚い）
```
#UseHook  
#NoEnv    
SendMode Input    
SetWorkingDir %A_ScriptDir%    
#SingleInstance, Force  
  
#IF, !IsGame()  
;---------------------------------  
; IME ON/OFF  
^D::IME_SET(1)  
^U::IME_SET(0)  
  
Tab & Space::Send, {Blind}{Tab}  
  
;---------------------------------  
; Tab＋IJKLで方向キー  
Tab & I::Send, {Blind}{Up}  
Tab & J::Send, {Blind}{Left}  
Tab & K::Send, {Blind}{Down}  
Tab & L::Send, {Blind}{Right}  
  
;---------------------------------  
; Tab＋P;['でHomeなど  
Tab & [::Send, {Blind}{PgUp}  
Tab & '::Send, {Blind}{PgDn}  
Tab & P::Send, {Blind}{Home}  
Tab & `;::Send, {Blind}{End}  
Tab & D::Send, {Blind}{Del}  
Tab & F::Send, !{F4}  
Tab & A::Send, {AppsKey}  
*^F::Send, {Blind}{z}  
*^E::Send, {Blind}{x}  
*^X::Send, {Blind}{e}  
*^Z::Send, {Blind}{f}  
Tab & Q::  
CoordMode, Mouse, Screen  
Click,1200,600  
Return  
  
Esc & S::  
Send, #{d}  
Sleep, 200  
Send, !{F4}  
Sleep, 100  
Send, {Up}  
Sleep, 100  
Send, {Enter}  
Return  
  
Tab & C::Send, #+{c}  
Tab & S::Send, #+{s}  
;---------------------------------  
; Ctrl＋数字キーでファンクションキー  
^1::Send, {F1}  
  
Return  
  
^2::Send, {F2}  
^3::Send, {F3}  
^4::Send, {F4}  
^5::Send, {F5}  
^6::Send, {F6}  
^7::Send, {F7}  
^8::Send, {F8}  
^9::Send, {F9}  
^0::Send, {F10}  
^-::Send, {F11}  
^=::Send, {F12}  
  
^R::  
If IsYMM4(){  
    Send, {1}  
    Sleep, 100  
    Send, {Esc}  
}  
Else {  
    Send, ^{r}  
}  
Return  
  
Tab & 1::AppActivate("C:\te220504\TE64.exe")  
Tab & 2::AppActivate("C:\Program Files (x86)\Microsoft\Edge\Application\msedge.exe")  
Tab & 3::AppActivate("C:\Users\nekom\AppData\Local\Programs\Microsoft VS Code\Code.exe")  
Tab & 4::AppActivate("C:\Users\nekom\AppData\Local\Obsidian\Obsidian.exe")   
Tab & 5::AppActivate("C:\Users\nekom\AppData\Local\Discord\app-1.0.9004\Discord.exe")  
Tab & 6::AppActivate("C:\Program Files\CELSYS\CLIP STUDIO 1.5\CLIP STUDIO PAINT\ClipStudioPaint.exe")  
  
Tab & R::AltTab  
Tab & E::ShiftAltTab  
  
  
AppActivate(appPath) {  
    appName:=RegExReplace(appPath, ".*\\", "")  
    Process,Exist,%appName%  
    If (ErrorLevel <> 0) {  
        WinGet, currentWindow, ProcessName, A  
        if (appName == currentWindow) {  
            WIN_SameAppNext()  
        }  
        else {  
            WinActivate,ahk_pid %ErrorLevel%  
        }  
    }  
    else {  
        Run, %appPath%  
    }  
}  
  
Tab & ]::WIN_SameAppNext()  
  
WIN_SameAppNext() {  
    WinGet, className, ProcessName, A  
    WinActivateBottom, ahk_exe %className%  
}  
#If  
#If, UseSpaceShortcut()  
  
UseAscii(key){  
    global ForceAscii  
    if ForceAscii && IME_GET() {  
        IME_SET(0)  
        Send, {Blind}{%key%}  
        IME_SET(1)    
    } else {  
        Send, {Blind}{%key%}  
    }  
}       
  
Tab & M::  
global ForceAscii  
ForceAscii := !ForceAscii  
if (ForceAscii){  
    SoundBeep , ,   
    Sleep, 50  
    SoundBeep , ,   
}  
else{  
    SoundBeep , ,   
}  
return  
  
Space::UseAscii("Space")  
*-::UseAscii("-")    
; *=::UseAscii("=")       
*[::UseAscii("[")    
*]::UseAscii("]")   
*;::UseAscii(";")   
*'::UseAscii("'")   
*,::UseAscii(",")    
*.::UseAscii(".")    
*/::UseAscii("/")    
*\::UseAscii("\")  
*1::UseAscii("1")  
*2::UseAscii("2")  
*3::UseAscii("3")  
*4::UseAscii("4")  
*5::UseAscii("5")  
*6::UseAscii("6")  
*7::UseAscii("7")  
*8::UseAscii("8")  
*9::UseAscii("9")  
*0::UseAscii("0")    
  
  
;------------------------------  
; Ctrl+Spaceで Esc & IMEをオフ  
^Space::  
if(IME_GET()){  
    Send, {ESC}  
    Sleep 1  
    IME_SET(0)  
} else {  
    Send, {Esc}  
}  
Return  
  
;-------------------------------  
; Shift+SpaceでBackSpace  
+Space::Send, {BS}  
^+Space::Send, ^{BS}  
  
  
Esc & D::  
FormatTime,TimeString,,yyyy-MM-dd  
Send,%TimeString%  
Return  
  
Esc & T::  
FormatTime,TimeString,,HH:mm  
Send,%TimeString%  
Return  
  
Esc & `;::  
FormatTime,TimeString,,yyMMddHHmmss  
Send,%TimeString%  
Return  
  
Esc & O::  
If IsEnglishVault(){  
    Send, - 日本語版{Enter}{Tab}a{Enter}{Enter}{Enter}---{Enter}{#}{#}{#}{#}{Space}  
}  
Else{  
    IME_SET(0)  
    FormatTime,TimeString,,HH:mm  
    Send,%TimeString%{Space}  
}  
Return  
  
#If  
  
UseSpaceShortcut(){  
    return !IsClipStudio() && !IsGame()  
}  
IsGame(){  
    WinGetActiveTitle title  
    return WinActive(ahk_exe Among Us.exe) != 0 || InStr(title, "Minecraft*")  
}  
IsClipStudio(){  
    WinGetActiveTitle title  
    Return InStr(title, "CLIP STUDIO PAINT")   
}  
IsEnglishVault(){  
    WinGetActiveTitle title  
    Return InStr(title, "english-note")  
}  
UseVimKeyBind(){  
    WinGetActiveTitle title  
    Return InStr(title, "Obsidian")  
}  
IsYMM4(){  
    WinGetActiveTitle title  
    Return InStr(title, "ゆっくりMovieMaker")  
}  
  
; https://w.atwiki.jp/eamat/pages/17.html からIME.ahkをダウンロード  
; IME_GET()とIME_SET()を以下にコピペする  
  
;-----------------------------------------------------------  
; IMEの状態の取得  
;   WinTitle="A"    対象Window  
;   戻り値          1:ON / 0:OFF  
;-----------------------------------------------------------  
  
IME_GET(WinTitle="A")  {  
    ControlGet,hwnd,HWND,,,%WinTitle%  
    if  (WinActive(WinTitle))   {  
        ptrSize := !A_PtrSize ? 4 : A_PtrSize  
        VarSetCapacity(stGTI, cbSize:=4+4+(PtrSize*6)+16, 0)  
        NumPut(cbSize, stGTI,  0, "UInt")   ;   DWORD   cbSize;  
        hwnd := DllCall("GetGUIThreadInfo", Uint,0, Uint,&stGTI)  
                 ? NumGet(stGTI,8+PtrSize,"UInt") : hwnd  
    }  
  
    return DllCall("SendMessage"  
          , UInt, DllCall("imm32\ImmGetDefaultIMEWnd", Uint,hwnd)  
          , UInt, 0x0283  ;Message : WM_IME_CONTROL  
          ,  Int, 0x0005  ;wParam  : IMC_GETOPENSTATUS  
          ,  Int, 0)      ;lParam  : 0  
}  
  
;-----------------------------------------------------------  
; IMEの状態をセット  
;   SetSts          1:ON / 0:OFF  
;   WinTitle="A"    対象Window  
;   戻り値          0:成功 / 0以外:失敗  
;-----------------------------------------------------------  
IME_SET(SetSts, WinTitle="A")    {  
    ControlGet,hwnd,HWND,,,%WinTitle%  
    if  (WinActive(WinTitle))   {  
        ptrSize := !A_PtrSize ? 4 : A_PtrSize  
        VarSetCapacity(stGTI, cbSize:=4+4+(PtrSize*6)+16, 0)  
        NumPut(cbSize, stGTI,  0, "UInt")   ;   DWORD   cbSize;  
        hwnd := DllCall("GetGUIThreadInfo", Uint,0, Uint,&stGTI)  
                 ? NumGet(stGTI,8+PtrSize,"UInt") : hwnd  
    }  
  
    return DllCall("SendMessage"  
          , UInt, DllCall("imm32\ImmGetDefaultIMEWnd", Uint,hwnd)  
          , UInt, 0x0283  ;Message : WM_IME_CONTROL  
          ,  Int, 0x006   ;wParam  : IMC_SETOPENSTATUS  
          ,  Int, SetSts) ;lParam  : 0 or 1  
}
```