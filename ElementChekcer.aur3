#Region Copyright
#cs
	Copyright (c) 2020, Sandra
#ce
#EndRegion Copyright

#include "wd_core.au3"
#include "wd_helper.au3"
#include <Clipboard.au3>
#include <String.au3>
#include <GuiEdit.au3>

#include <ButtonConstants.au3>
#include <ComboConstants.au3>
#include <EditConstants.au3>
#include <GUIConstantsEx.au3>
#include <WindowsConstants.au3>
#Region ### START Koda GUI section ### Form=C:\Users\Sandr\Dropbox\Autoit\Form Project\element checker 4.kxf
$Form1_1 = GUICreate("Element Checker", 258, 568, -1, -1, -1, BitOR($WS_EX_TOPMOST, $WS_EX_WINDOWEDGE))
GUISetIcon("C:\Users\Sandr\Dropbox\IconPacks\Plus.ico", -1)
GUISetBkColor(0x008000)
$IWeb = GUICtrlCreateInput("", 8, 8, 153, 21)
$Button1 = GUICtrlCreateButton("Search", 168, 8, 75, 25)
$IPath = GUICtrlCreateInput("", 8, 80, 241, 21)
$Combo1 = GUICtrlCreateCombo("", 8, 112, 153, 25, BitOR($CBS_DROPDOWN, $CBS_AUTOHSCROLL))
GUICtrlSetData($Combo1, "Active|Attribute|Clear|Click|CSS|Displayed|Enabled|Name|Property|Rect|Screenshot|Selected|Text|Value", "Click")
$IPath1 = GUICtrlCreateInput("", 8, 144, 73, 21)
$IPath2 = GUICtrlCreateInput("", 88, 144, 73, 21)
$Button3 = GUICtrlCreateButton("Bismillah", 9, 177, 115, 25)
$Button4 = GUICtrlCreateButton("Write", 129, 177, 123, 25)
$Button5 = GUICtrlCreateButton("Clear", 176, 136, 75, 33)
$IPathName = GUICtrlCreateInput("", 8, 48, 241, 21)
$Edit1 = GUICtrlCreateEdit("", 8, 352, 241, 145)
GUICtrlSetData(-1, "")
$INamaFile = GUICtrlCreateInput("", 8, 320, 241, 21)
$Button6 = GUICtrlCreateButton("Save", 8, 504, 65, 25)
$Button7 = GUICtrlCreateButton("Open", 90, 505, 73, 25)
$Clipboard = GUICtrlCreateInput("", 8, 536, 241, 21)
$Button8 = GUICtrlCreateButton("OpenLOG", 176, 504, 75, 25)
$Radio1 = GUICtrlCreateRadio("1", 176, 112, 33, 17)
$Radio2 = GUICtrlCreateRadio("2", 216, 112, 33, 17)
$Edit2 = GUICtrlCreateEdit("", 8, 208, 241, 97)
GUICtrlSetData(-1, "Edit2")
GUISetState(@SW_SHOW)
#EndRegion ### END Koda GUI section ###

Local $sDesiredCapabilities, $sSession
SetupGecko()
$_WD_DEBUG = True
_WD_Startup()
$sSession = _WD_CreateSession($sDesiredCapabilities)

While 1
	$nMsg = GUIGetMsg()
	Switch $nMsg
		Case $GUI_EVENT_CLOSE
			_WD_Window($sSession, 'Close')
			_WD_Shutdown()
			Exit
		Case $Button1
			$web = GUICtrlRead($IWeb)
			_WD_Navigate($sSession, $web)
		Case $Button5
			ControlSetText("Element Checker", "", 12, "")
			ControlSetText("Element Checker", "", 5, "")
			ControlSetText("Element Checker", "", 7, "")
			ControlSetText("Element Checker", "", 8, "")
		Case $Button3
			$namaweb = StringReplace(StringReplace($web, "/", "`"), ":", ")")
			$namaoutputlog = 'LOG EC + ' & $namaweb & ' ' & @MDAY & '-' & @MON & '-' & @YEAR & '.txt'
			If GUICtrlRead($Radio1) = $GUI_CHECKED Then
				$path = GUICtrlRead($IPath)
				$sComboRead = GUICtrlRead($Combo1)
				$sButton = _WD_FindElement($sSession, $_WD_LOCATOR_ByXpath, $path)
				$waktuz = _WD_ElementAction($sSession, $sButton, $sComboRead)

				ControlSetText("Element Checker", "", 21, "")
				_GUICtrlEdit_InsertText(21, $waktuz & @CRLF, 0)
				FileWrite(@ScriptDir & "\LOG CHECKER\" & $namaoutputlog, $path & @CRLF)
				FileWrite(@ScriptDir & "\LOG CHECKER\" & $namaoutputlog, $sComboRead & @CRLF)
				FileWrite(@ScriptDir & "\LOG CHECKER\" & $namaoutputlog, $waktuz & @CRLF)
			ElseIf GUICtrlRead($Radio2) = $GUI_CHECKED Then
				$path = GUICtrlRead($IPath)
				$path1 = GUICtrlRead($IPath1)
				$path2 = GUICtrlRead($IPath2)
				$sButton = _WD_FindElement($sSession, $_WD_LOCATOR_ByXpath, $path)
				$waktuz = _WD_ElementAction($sSession, $sButton, $path1, $path2)

				ControlSetText("Element Checker", "", 21, "")
				FileWrite(@ScriptDir & "\LOG CHECKER\" & $namaoutputlog, $path & @CRLF)
				FileWrite(@ScriptDir & "\LOG CHECKER\" & $namaoutputlog, $path1 & "," & $path2 & @CRLF)
				FileWrite(@ScriptDir & "\LOG CHECKER\" & $namaoutputlog, $waktuz & @CRLF)
			EndIf
		Case $Button4
			If GUICtrlRead($Radio1) = $GUI_CHECKED Then
				$path = "'" & GUICtrlRead($IPath) & "'"
				$sComboRead = "'" & StringLower(GUICtrlRead($Combo1)) & "'"
				$pathName = GUICtrlRead($IPathName)

				_GUICtrlEdit_InsertText(13, '_GUICtrlEdit_InsertText($idlogproses, ' & "'" & $pathName & "...')" & @CRLF)
				_GUICtrlEdit_InsertText(13, '$sButton = _WD_FindElement($sSession, $_WD_LOCATOR_ByXpath, ' & $path & ') ; ' & $pathName & " " & $web & @CRLF)
				_GUICtrlEdit_InsertText(13, '$' & $pathName & ' = _WD_ElementAction($sSession, $sButton, ' & $sComboRead & ') ; ' & $web & @CRLF)
				_GUICtrlEdit_InsertText(13, ';hasil text = -' & $waktuz & '-' & @CRLF)
				_GUICtrlEdit_InsertText(13, 'sleep(1000)' & @CRLF)
			ElseIf GUICtrlRead($Radio2) = $GUI_CHECKED Then
				$path = "'" & GUICtrlRead($IPath) & "'"
				$path1 = "'" & GUICtrlRead($IPath1) & "'"
				$path2 = "'" & GUICtrlRead($IPath2) & "'"
				$pathName = GUICtrlRead($IPathName)

				_GUICtrlEdit_InsertText(13, '_GUICtrlEdit_InsertText($idlogproses, ' & "'" & $pathName & "...')" & @CRLF)
				_GUICtrlEdit_InsertText(13, '$sButton = _WD_FindElement($sSession, $_WD_LOCATOR_ByXpath, ' & $path & ') ; ' & $pathName & " " & $web & @CRLF)
				_GUICtrlEdit_InsertText(13, '_WD_ElementAction($sSession, $sButton, ' & $path1 & ',' & $path2 & ') ; ' & $web & @CRLF)
				_GUICtrlEdit_InsertText(13, 'sleep(1000)' & @CRLF)
			EndIf
		Case $Button6
			$path = GUICtrlRead($Edit1)
			$namaFile = GUICtrlRead($INamaFile)
			FileWrite(@ScriptDir & "\" & $namaFile & ' + ' & $namaweb & ' ' & @MDAY & '-' & @MON & '-' & @YEAR & '.txt', $path & @CRLF)
		Case $Button7
			Run("explorer.exe " & @ScriptDir)
		Case $Button8
			Run("explorer.exe " & @ScriptDir & "\LOG CHECKER\")
	EndSwitch
WEnd

Func _ChromeSetInputValueById($sSession, $Id, $Value)
	$sButton = _WD_FindElement($sSession, $_WD_LOCATOR_ByXpath, "//input[@id='" & $Id & "']")
	_WD_ElementAction($sSession, $sButton, 'value', $Value)
EndFunc   ;==>_ChromeSetInputValueById

Func SetupGecko()
	_WD_Option('Driver', 'geckodriver.exe')
	_WD_Option('DriverParams', '--log trace')
	_WD_Option('Port', 4444)

	$sDesiredCapabilities = '{"desiredCapabilities":{"javascriptEnabled":true,"nativeEvents":true,"acceptInsecureCerts":true}}'
EndFunc   ;==>SetupGecko

Func SetupIE()
	_WD_Option('Driver', 'IEDriverServer.exe')
	_WD_Option('Port', 5555)
	_WD_Option('DriverParams', '--log-file=' & @ScriptDir & '\IE.log')
	$sDesiredCapabilities = '{"desiredCapabilities":{"javascriptEnabled":true,"nativeEvents":true,"acceptInsecureCerts":true}}'
EndFunc   ;==>SetupIE

Func SetupChrome()
	_WD_Option('Driver', 'chromedriver.exe')
	_WD_Option('Port', 9515)
	_WD_Option('DriverParams', '--log-path=' & @ScriptDir & '\chrome.log')
	$sDesiredCapabilities = '{"capabilities": {"alwaysMatch": {"goog:chromeOptions": {"w3c": true }}}}'
EndFunc   ;==>SetupChrome

Func SetupEdge()
	_WD_Option('Driver', 'msedgedriver.exe')
	_WD_Option('Port', 9515)
	_WD_Option('DriverParams', '--verbose')
	$sDesiredCapabilities = '{"capabilities":{}}'
	;$sDesiredCapabilities = '{"capabilities": {"alwaysMatch": {"ms:edgeOptions": {"binary": "' & StringReplace(@UserProfileDir, "\", "/") & '/AppData/Local/Microsoft/Edge SxS/Application/msedge.exe"}}}}'
EndFunc   ;==>SetupEdge
