@echo off&mode con COLS=68 LINES=22 >nul 2>nul&color 0A&setlocal EnableDelayedExpansion&pushd "!Windir!\Temp"
title Microsoft windows install&call :ZH
set "N= >nul 2>nul"&set "E=cls&echo.&echo.          "&set "E1=!E: =!"&set "E2=!E1:cls=!"&set "G=&pause>nul&goto :End"&set "b=bcdedit"&set "bs=bcdedit /set"&set "WS=!Windir!\System32"&set "WT=!Windir!\Temp"&set "AC="!WT!\aria2c.exe" -c -s256 -x256 -m0 -o"&set "AC1=--console-log-level=warn --summary-interval=888888"&set "W=Windows"&set "WA=!WS!\config\AutoSys"&set "WW=http://win11.link/"
if exist "!WS!\find.exe" (set "Find=find /i ") else set "Find=findstr /i /C:"
if exist "!WS!\chcp.com" chcp|%Find%"936"%N%||chcp 437%N%&&call :EN
"!WS!\FLTMC.exe"%N%||(%E1%!T15!...%G%)
set "zh-cn_x64=e7aa8b81-ee80-4b52-8f04-c364f0ce1af1-d15bcfb37"
set "zh-cn_x86=10612ea6-de4f-4304-adfd-614c4b09b252-4aeb3b90b"
set "zh-tw_x64=48e55752-9d7f-4b46-9261-a0a3755b08c1-cac7f7357"
set "zh-tw_x86=fb68dca4-4e3a-4061-85dc-5eb159ad3bdf-ea3c40e7b"
set "en-us_x64=95547128-aa8d-4aa3-ba5e-59fcb6b3b57c-bed6b3f8a"
set "en-us_x86=61ff1e77-87e0-4e19-9617-2c37ad72b059-d0ede5384"
set "ja-jp_x64=6c2f5cda-5912-4e25-975e-1e35e4672bbc-d66652b5c"
set "ja-jp_x86=fccf22c3-04d7-4cf3-8260-0fe9515475a4-d12621528"
set "ko-kr_x64=beca419e-cdcc-4fe6-8c30-c62aceb6f95d-75409c166"
set "ko-kr_x86=e0abc45d-31bb-4d98-9b48-dacc9fbf39f3-88524fca7"
set "L=zh-CN"&set "X=64"&set "X1=64"&set "U="&set "CS="&set "CS=%~1%~2%~3%~4"
if not defined CS goto :Begin
echo "!CS!"|%Find%"32"%N%&&set "X=86"&&set "X1=32"
echo "!CS!"|%Find%"#C"%N%&&set "Clear=Yes"
for %%i in (zh-CN zh-TW en-US ja-JP ko-KR) do echo "!CS!"|%Find%"%%i"%N%&&set "L=%%i"&&goto :Next
:Next
if defined CS set "CS=!CS:32=!"
if defined CS set "CS=!CS:64=!"
if defined CS set "CS=!CS:%L%=!"
echo "!CS!"|%Find%"#u"%N%&&set "U=u"
echo "!CS!"|%Find%"#a"%N%&&set "U=a"
if not defined U set "U="
if defined CS set "CS=!CS:#%U%=!"
if defined CS set "F=!CS!"
set "LX=!%L%_x%X%!"&set "M=!LX:~-9!"&set "LX=!LX:~0,-10!"
:Begin
cls&echo.
echo.  [1]  !W! 7   !T16! !X1!!T6! !L!
echo.
echo.  [2]  !W! 8.1 !T11! !X1!!T6! !L!
echo.
echo.  [3]  !W! 10  !T9! !X1!!T6! !L!
echo.
echo.  [4]  !W! 10  !T10! !X1!!T6! !L!
echo.
echo.  [5]  !W! 10  !T11! !X1!!T6! !L!
echo.
echo.  [6]  !W! 11  !T9! 64!T6! !L!
echo.
echo.  [7]  !W! 11  !T10! 64!T6! !L! 
echo.
echo.  [8]  !W! 11  !T11! 64!T6! !L!
echo.
echo.  [X]  !T12!
echo.
set "Name=!W!10_21h2_x!X!_!L!.esd"&set "Os=10"&set "URL=http://dl.delivery.mp.microsoft.com/filestreamingservice/files/!LX!/19044.1288.211006-0501.21h2_release_svc_refresh_CLIENTCONSUMER_RET_x!X!FRE_!L!.esd"
choice /?%N%||(
	set /p "errorlevel=_______!T5!:"
	if /i "!errorlevel!"=="x" goto :End
	%Find%"[!errorlevel!]" "%0"%N%||(%E1%!!T7!"!errorlevel!"!T8!...&pause>nul&goto :Begin)
)
choice /?%N%&&choice /c:12345678X /n /m "_______!T5!:"
set "C=!errorlevel!"
if "!C!"=="9" goto :End
if !C! GTR 5 set "M=aa45fb329"&&set "Name=!W!11_!L!.esd"&&set "Os=11"&&set "URL=http://dl.delivery.mp.microsoft.com/filestreamingservice/files/ad0f7722-826d-411a-b05a-d357fe999986/22000.194.210913-1444.co_release_svc_refresh_CLIENTCONSUMER_RET_x64FRE_zh-cn.esd"
if "!C!"=="8" set "I=7"
if "!C!"=="7" set "I=6"
if "!C!"=="6" set "I=4"
if "!C!"=="5" set "I=6"
if "!C!"=="4" set "I=5"
if "!C!"=="3" set "I=4"
if "!L!"=="zh-CN" (
	if "!C!"=="5" set "I=7"
	if "!C!"=="4" set "I=6"
	if "!C!"=="3" set "I=4"
)
if "!L!"=="en-US" (
	if "!C!"=="5" set "I=9"
	if "!C!"=="4" set "I=7"
	if "!C!"=="3" set "I=4"
)
if "!C!"=="2" set "M=875c89322"&&set "I=4"&&set "Name=!W!8.1_x!X!.esd"&&set "Os=8.1"&&set "81=c8e8bf1cb11a61cba40a4ebcbbb5bf8cc49426bd"&&(if "!X!"=="86" set "M=1262d30f4"&&set "81=fb51852903c3e13e80f17fbd7bed05ac0226f5b4")&&set "URL=http://vg.dl.ws.microsoft.com/dl/content/c/updt/2015/01/9600.17053.winblue_refresh.141120-0031_x!X!fre_client_core_zh-cn-ir5_ccra_x!X!frer_zh-cn_esd_!81!.esd"
if "!C!"=="1" set "M=249da244a"&&set "I=1"&&set "Name=!W!7.esd"&&set "Os=7"&&set "URL=!WW!7"&&(if "!X!"=="86" set "I=2")&&ver|%Find%"6.1."%N%||(%E%!T17!...&pause>nul&goto :Begin)
%E%提醒：重装系统会清空C盘,C盘之外的磁盘无影响。%E2%         如C盘包括桌面有资料需要,请备份至C盘之外的磁盘。%E2%                请按任意键继续...或关闭窗口...&pause>nul
call :TP
%E%!T3!...
md "!WT!\aria2"%N%
!WT!\aria2c.exe -h%N%||(ver|%Find%"6.1."%N%&&bitsadmin /transfer "" !WW!a !WT!\aria2c.Exe%N%||powershell -Command "(New-Object Net.WebClient).DownloadFile('!WW!a1', '"!WT!\aria2c.Exe"')"%N%)
%E%   !T1!...&echo.
!WT!\aria2c.exe -h%N%||(%E1%      !T2!...%G%)
!AC! "Md5.exe" !AC1! "!WW!m" -d "!WT!"%N%
!AC! "!Name!" !AC1! "!URL!" -d "!TP!"
%E%   !T1!...&echo.
!AC! "boot.Wim" !AC1! "!WW!t" -d "!WT!"
%E%   !T1!...&echo.
!AC! "boot.Sdi" !AC1! "!WW!s" -d "!WT!"%N%
:: if not "!errorlevel!"=="0" (%E%   !T2!...%G%)
!AC! "WimEsd.DLL" !AC1! "!WW!-" -d "!WT!"%N%
%E%!T19!...&Md5 "!TP!\!Name!"|%Find%"!M!"%N%||(del /f /q "!TP!\!Name!"%N%&%E1%      !T18!...%G%)
if "!Os!"=="8.1" !AC! "W8.exe" !AC1! "!WW!w8" -d "!WT!"%N%&&W8 "!TP!\!Name!"%N%
set "BcdID=!random:~0,3!!random:~0,2!"&set "BcdID1=fff-9d96-11de-8e71-fffffffffff"&set "BN=Microsoft !W! install"
set "i1={!BcdID!!BcdID1!a}"
set "i2={!BcdID!!BcdID1!b}"
!b! /default {current}%N%
for /f "tokens=2" %%a in ('!b!^|%Find%"!BcdID1!a"') do !b! /delete %%a /cleanup%N%
!b! /create !i2! /d "!BN!" /device%N%
!bs! !i2! ramdisksdidevice partition=!SystemDrive!%N%
!bs! !i2! ramdisksdipath "\!W!\Temp\BOOT.SDI"%N%
!b! /create !i1! /d "!BN!" /application osloader%N%
!bs! !i1! device ramdisk="[!SystemDrive!]\!W!\Temp\BOOT.WIM",!i2!%N%
!bs! !i1! osdevice ramdisk="[!SystemDrive!]\!W!\Temp\BOOT.WIM",!i2!%N%
!bs! !i1! path \!W!\system32\boot\winload.exe%N%
!b!|%Find%"winload.efi"%N%&&!bs! !i1! path \!W!\system32\boot\winload.efi%N%
!bs! !i1! description "!BN!"%N%
!bs! !i1! locale zh-CN%N%
!bs! !i1! inherit {bootloadersettings}%N%
!bs! !i1! systemroot \!W!%N%
!bs! !i1! detecthal Yes%N%
!bs! !i1! winpe Yes%N%
!bs! !i1! ems no%N%
!b! /displayorder !i1! /addlast%N%
!b! /default !i1!%N%
!b! /timeout 2%N%
echo SysFile=!TP!\!Name!>"!WA!"
echo Os=!Os!>>"!WA!"
echo Index=!I!>>"!WA!"
if /i "!U!"=="a" echo Unattend=a>>"!WA!"
if /i "!U!"=="u" echo Unattend=u>>"!WA!"
if defined F echo User=!F!>>"!WA!"
echo Language=!L!>>"!WA!"
if !cSpace! lss 12 echo Format=Yes>>"!WA!"
if /i "!Clear!"=="Yes" echo Clear=Yes>>"!WA!"
%E%    !T4!...%G%
:TP
for %%i in (C D E F G H I J K L M N O P Q R S T U V W Y) do (
	if exist %%i: (
		echo 1 >%%i:\CMDPE.COM
		for /f "skip=7 tokens=3" %%j in ('dir /-c /w %%i:\CMDPE.COM') do (
			del %%i:\CMDPE.COM%N%
			set "Space=%%j"
			set "Space=!Space:~0,-9!"
			if /i "%%i:"=="!SystemDrive!" (
				set "cSpace=!Space!"
				if !Space! lss 16 set "Space="
			)
			if !space! gtr !MaxSpace! set "MaxSpace=!Space!"&&set "TP=%%i:"
		)
	)
)
if not defined TP (%E1%!T14!...%G%)
if !MaxSpace! lss 5 (%E1%!T13!...%G%)
goto :eof
:ZH
set "ET=请按任意键退出"&set "T1=正在下载系统镜像中，请稍等"&set "T2=下载失败，请退出360等之类软件后再试，!ET!"&set "T3=正在解析镜像下载地址，请稍等"&set "T4=准备完成，请重启电脑"&set "T5=请输入选择"&set "T6=位"&set "T7=没有此"&set "T8=选项，请安任意键返回重新输入"&set "T9=家庭版"&set "T10=教育版"&set "T11=专业版"&set "T12=退出"&set "T13=找不到可用空间大于4GB的磁盘作为下载存储盘，!ET!"&set "T14=找不到可用的磁盘作为下载存储盘，!ET!"&set "T15=请以管理员身份运行CMD命令提示符，!ET!"&set "T16=旗舰版"&set "T17=此电脑不建议安装!W!7，请按任意键返回"&set "T18=系统镜像校验不正确，请重新下载，!ET!"
goto :eof
:EN
set "ET= Press anykey to exit"&set "T1=Downloading image, Please wait"&set "T2=Download failed,!ET!"&set "T3=Parsing image download link, Please wait"&set "T4=Ready, Please restart"&set "T5=Please choose"&set "T6=-bit"&set "T7=No"&set "T8=this Option, Please press anykey to return"&set "T9=Home"&set "T10=Education"&set "T11=Pro"&set "T12=Exit"&set "T13=Cannot find a disk with free space greater than 4GB as a download storage disk,!ET!"&set "T14=Cannot find a download available disk storage disk,!ET!"&set "T15=Please run as administrator CMD,!ET!"&set "T16=Ultimate"&set "T17=This computer does not recommend installing !W!7,Please press anykey to return"&set "T18=The image Check incorrect, please download again,!ET!"
goto :eof
:End
cls&del 1.cmd 2>nul&Exit
