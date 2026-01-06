---
layout: ../../layouts/MarkdownPostLayout.astro
title: "Delphi调用COM"
description: "delphi6/7"
date: 2020-05-14
author: "tdtc"
---

# 准备
## 1. Windows 系统引入
运行 -> Regsvr32 x:/FCV.dll

## 2. Delphi 引入
Project -> Import Type Library ->"FCV 1.1 Type Library (Version1.1)"

# code

```Delphi
unit
    UntMain; interface uses Windows, Messages, SysUtils, Variants, Classes,
	Graphics, Controls, Forms, Dialogs, StdCtrls, OleServer, FCVLib_TLB;

type
  TfrmMain = class(TForm)
	lblFileVal: TLabel;
	lblFcvVal: TLabel;
	edtFilePath: TEdit;
	btnGenFCN: TButton;
	edtFCVpath: TEdit;
	btnCalFileValue: TButton;
	btnReadFCV: TButton;
	btnCreatFCV: TButton;
	UCRC321: TUCRC32;
	procedure btnCreatFCVClick(Sender: TObject);
	procedure btnGenFCNClick(Sender: TObject);
	procedure btnCalFileValueClick(Sender: TObject);
	procedure btnReadFCVClick(Sender: TObject);
  private
      { Private declarations }
      myFCV: IUCRC32;
  public
      { Public declarations }
      instanceFlag: Boolean;

end;

var
    frmMain: TfrmMain;  

implementation
    {$R *.dfm}

	procedure TfrmMain.btnCreatFCVClick(Sender: TObject);
	begin
		myFCV:= CoUCRC32.Create;
		instanceFlag := True;
	end;

	procedure TfrmMain.btnGenFCNClick(Sender: TObject);
	var
	    saveFile, checkFile: WideString; i112: Integer;
	begin
	    //
		if not instanceFlag then exit;
		saveFile:= edtFCVpath.Text;
		checkFile:= edtFilePath.Text;
		i112:= myFCV.SaveFCN(saveFile, checkFile);
		ShowMessage(inttostr(i112));
	end;

	procedure TfrmMain.btnCalFileValueClick(Sender: TObject);
	var
	    filePath: WideString;
		retVal: DWORD;
	begin
	    if not instanceFlag then exit;
		filePath:= edtFilePath.Text;
		retVal:= myFCV.CalCRC32(filePath);
		lblFileVal.Caption:= IntToHex(retVal, 8);
	end;

	procedure TfrmMain.btnReadFCVClick(Sender: TObject);
	var
	  filePath: WideString;
		retVal: DWORD;
	begin
	//
		if not instanceFlag then exit;
		filePath:= edtFCVpath.Text;
		retVal:= myFCV.ReadFCN(filePath);
		lblFcvVal.Caption:= IntToHex(retVal, 8);
	end;

end.
```
