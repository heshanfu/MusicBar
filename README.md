<p align="center">
  <img src="https://github.com/emadabdalrahman/MusicBar/blob/master/ScreenShots/sound-bars-pulse.png?raw=true" alt="MusicBar Logo"/>
</p>

# MusicBar  [ ![Download](https://api.bintray.com/packages/emad/maven/MusicBar/images/download.svg) ](https://bintray.com/emad/maven/MusicBar/_latestVersion)

![](https://github.com/emadabdalrahman/MusicBar/blob/master/ScreenShots/full-optimize.gif?raw=true)

## Setup

```groovy
dependencies {
      implementation 'com.oze.music:MusicBar:1.0.0'
}
```
## Usage

Function | Description
------------ | -------------
setAnimationChangeListener(OnMusicBarAnimationChangeListener listener) | animation listener
setProgressChangeListener(OnMusicBarProgressChangeListener listener) | progress listener
removeAllListener() | remove Progress and Animation listener
loadFrom(byte[] file, int durationInSec) | load from music file as byte[] with duration in sec
show() | start show animation
hide() | start hide animation
setProgress(int position) | move to specified position (in milisecand) 
getPosition() | return current progress position
setLoadedBarColor(int color) | change progressed bar color **default RED**
setBackgroundBarColor(int color) | change unprogressed bar color **default #dfd6d6**
setSpaceBetweenBar(int spaceBetweenBar) | change distance between bars (in px) **default 2**
setBarWidth(float barWidth) | change bar width (in px) **default 2** 


**XML** 

for BigMusicBar

![BigMusicBar](https://github.com/emadabdalrahman/MusicBar/blob/master/ScreenShots/BigMusicBar.png?raw=true)
```XML
   <com.oze.music.musicbar.BigMusicBar
        android:id="@+id/BigMusicBar"
        android:layout_width="match_parent"
        android:layout_height="200dp"
        android:background="@android:color/white"
        android:padding="8dp" />
```
OR MiniMusicBar 

![MiniMusicBar](https://github.com/emadabdalrahman/MusicBar/blob/master/ScreenShots/MiniMusicBar.png?raw=true) 
```XML
    <com.oze.music.musicbar.MiniMusicBar
        android:id="@+id/MiniMusicBar"
        android:layout_width="match_parent"
        android:layout_height="80dp"
        android:padding="8dp"
        android:background="@android:color/white" />
```
**Java**
```java
 @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
        
        BigMusicBar musicBar = findViewById(R.id.BigMusicBar);
        //or  
        MiniMusicBar musicBar = findViewById(R.id.MiniMusicBar);
        
        //add animation listener
        musicBar.setAnimationChangeListener(mOnMusicBarAnimationChangeListener);
        
        //add progress listener
        musicBar.setProgressChangeListener(mOnMusicBarProgressChangeListener);
        
        //change progress 
        musicBar.setProgress(50)
        
        //start show animation
        musicBar.show()
        
        //start hide animation
        musicBar.hide()
        
        //change bar width
        musicBar.setBarWidth(2);
        
        //change Space Between Bars
        musicBar.setSpaceBetweenBar(2); //Recommend to make barWidth equal spaceBetweenBar
    }

```


**AnimationListener**
```Java
MusicBar.OnMusicBarAnimationChangeListener mOnMusicBarAnimationChangeListener = new MusicBar.OnMusicBarAnimationChangeListener() {
        @Override
        public void onHideAnimationStart() {
            Log.i(TAG, "onHideAnimationStart");
        }

        @Override
        public void onHideAnimationEnd() {
            Log.i(TAG, "onHideAnimationEnd");
        }

        @Override
        public void onShowAnimationStart() {
            Log.i(TAG, "onShowAnimationStart");

        }

        @Override
        public void onShowAnimationEnd() {
            Log.i(TAG, "onShowAnimationEnd");
        }
    };
```
**ProgressListener**
```Java
 MusicBar.OnMusicBarProgressChangeListener mOnMusicBarProgressChangeListener = new MusicBar.OnMusicBarProgressChangeListener() {
        @Override
        public void onProgressChanged(MusicBar musicBar, int progress, boolean fromUser) {
            Log.i(TAG, "onProgressChanged");
        }

        @Override
        public void onStartTrackingTouch(MusicBar musicBar) {
         Log.i(TAG, "onStartTrackingTouch");
        }

        @Override
        public void onStopTrackingTouch(MusicBar musicBar) {
            Log.i(TAG, "onStopTrackingTouch");
        }
    };
```
**animation**

![animation](https://github.com/emadabdalrahman/MusicBar/blob/master/ScreenShots/animation-optimize.gif?raw=true)
