# Adapter Pattern

![Diagram of Adapter Pattern](https://www.tutorialspoint.com/design_pattern/images/adapter_pattern_uml_diagram.jpg)

### MediaPlayer.java  

```java
public interface MediaPlayer {
	public void play(String audioType, String fileName);
}
```

### AdvancedMediaPlayer.java 

```java
public interface AdvancedMediaPlayer {	
	public void playVlc(String fileName);
	public void playMp4(String fileName);
}
```

### VlcPlayer.java  

```java
public class VlcPlayer implements AdvancedMediaPlayer{
	@Override
	public void playVlc(String fileName) {
		System.out.println("Playing vlc file. Name: "+ fileName);		
	}

	@Override
	public void playMp4(String fileName) {
		// do nothing
	}
}
```

### Mp4Player.java 

```java
public class Mp4Player implements AdvancedMediaPlayer{
	@Override
	public void playVlc(String fileName) {
		// do nothing
	}

	@Override
	public void playMp4(String fileName) {
		System.out.println("Playing mp4 file. Name: "+ fileName);		
	}
}
```

### MediaAdapter.java 

```java
public class MediaAdapter implements MediaPlayer {
	AdvancedMediaPlayer advancedMusicPlayer;

	public MediaAdapter(String audioType) {   
		if (audioType.equalsIgnoreCase("vlc")) {
			advancedMusicPlayer = new VlcPlayer();			
		}
		else if (audioType.equalsIgnoreCase("mp4")) {
			advancedMusicPlayer = new Mp4Player();
		}	
	}

	@Override
	public void play(String audioType, String fileName) {
		if (audioType.equalsIgnoreCase("vlc")) {
			advancedMusicPlayer.playVlc(fileName);
		}
		else if (audioType.equalsIgnoreCase("mp4")) {
			advancedMusicPlayer.playMp4(fileName);
		}
	}
}
```

### AudioPlayer.java  

```java
public class AudioPlayer implements MediaPlayer {
	MediaAdapter mediaAdapter; 

	@Override
	public void play(String audioType, String fileName) {		
		// Inbuilt support to play mp3 music files
		if (audioType.equalsIgnoreCase("mp3")){
			System.out.println("Playing mp3 file. Name: " + fileName);			
		} 
      
		// MediaAdapter is providing support to play other file formats
		else if (audioType.equalsIgnoreCase("vlc") || audioType.equalsIgnoreCase("mp4")) {
			mediaAdapter = new MediaAdapter(audioType);
			mediaAdapter.play(audioType, fileName);
		}
      
		else {
			System.out.println("Invalid media. " + audioType + " format not supported");
		}
	}   
}
```

### AdapterPatternDemo.java 

```java
public class AdapterPatternDemo {
	public static void main(String[] args) {
		AudioPlayer audioPlayer = new AudioPlayer();

		audioPlayer.play("mp3", "Sajjan Raj Vaidya - Chitthi Vitra.mp3");
		audioPlayer.play("mp4", "James Arthur - Say You Won't Let Go.mp4");
		audioPlayer.play("vlc", "Ritviz - Sage.vlc");
		audioPlayer.play("avi", "Imagine Dragons - Not Today.avi");
	}
}
```

