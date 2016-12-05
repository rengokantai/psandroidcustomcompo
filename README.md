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
  try{
    PackageInfo packageInfo = getContext().getPackageManager().getPackageInfo(getContext().getPackageName(),0);
    //textView.setText(packageInto.versionName);
    setText(packageInto.versionName);
    }catch(PackageManager.NameNotFoundException e){}
  }
}
```


###4 Use Custom View in Java
MainActivity.java
```
VersionView view = new VersionView(this);
setContentView(view);
```
VersionView.java
```
public class VersionView extends TextView{
  public VersionView(Context context){super(context);setVersion();}  //for java
  public VersionView(Context context,AttributeSet attrs){super(context,attrs);setVersion();}  //for java
  public VersionView(Context context,AttributeASet attrs,int defStyle){super(context,attrs,defStyle);setVersion();}  //for java
  //refactor the code into here , note getContext()
  private void setVersion(){
  try{
    PackageInfo packageInfo = getContext().getPackageManager().getPackageInfo(getContext().getPackageName(),0);
    //textView.setText(packageInto.versionName);
    setText(packageInto.versionName);
    }catch(PackageManager.NameNotFoundException e){}
    
    
    //add this line
    setBackgroundColor(Color.RED);
  }
}
```


###5 Use Custom View in XML
activity_main.xml
```
<com.yd.versionview.VersionView ...
```
change back:
```
setContentView(R.layout.activity_main);
```


###6 Specify Parent Parameters in XML
```
<com.yd.versionview.VersionView ...android:textColor="#010"
```




##3. Compound Control
###2 Create a Custom Compound Control
MainActivity.java
```
View.OnClickListener listener = (v)->{
  switch(v.getId()){
    case R.id.plus:
      numInches++;
      updateControls();
  }
}
mPlusButton.setOnClickListener(listener);



piivate void updateControls(){
  int feet = numInches/12;
  int inches = mNumInches %12;
  String text = String.format("%d %d\"",feet,inches);
  mTextView.setText(text);
  mMinusButton.setEnabled(mNumInches>0);
}

```
LengthPicker.java
```

//05:41
privatye void init(){
LayoutInflater inflater = LayoutInflater.from(getContext());
inflater.inflate(R.layout.length_picker,this);
setContentView(R.layout.activity_main);
}
public class LengthPicker extends LinearLayout{
public LengthPicker(Context context){
  super(context);
}
public LengthPicker(Context contexst,AttrbuteSet attrs){
  super(context,attrs);
}
}
```


##8. dispatchDraw
###1 Overview
####01:10
Rotated LinearLayout = sidewaysLayout  

####01:32 how?
override onMeasure first, then override dispatchDraw

###2 SidewaysLayout

 













##9. Fragment vs. Custom View
###1 Fragment vs. Custom View
- Customize
- size (onMeasure)
- position (onLayout)
- appearance(onDraw)


Fragment:
- take photo( onActivityResult)
- Menu button(onCreateOptionsMenu)

Custom View
- show photo 4:3 (onMeasure)
- Fanout photos (onLayout)
- histogram (onDraw)

