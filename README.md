# psandroidcustomcompo
##1. Introduction
###1 Overview
####03:37
Techniques
- shortcut View and ViewGroup
- Custom View
- Custom ViewGroup



##2. Extend a Simple View
###2 Show Version in Hello World
```
TextView textView = (TextView) findViewById(R.id.text);
try{
  PackageInfo packageInfo = getPackageManager().getPackageInfo(getPackageName(),0);
  textView.setText(packageInto.versionName);
}catch(){
}
```


###3 Create Custom View
VersionView.java
```
public class VersionView extends TextView{
  public VersionView(Context context){super(context);setVersion();}  //for java
  public VersionView(Context context,AttributeSet attrs){super(context,attrs);setVersion();}  //for java
  public VersionView(Context context,AttributeASet attrs,int defStyle){super(context,attrs,defStyle);setVersion();}  //for java
  //refactor the code into here , note getContext()
  private void setVersion(){
    PackageInfo packageInfo = getContext().getPackageManager().getPackageInfo(getContext().getPackageName(),0);
    //textView.setText(packageInto.versionName);
    setText(packageInto.versionName);
  }
}
```
