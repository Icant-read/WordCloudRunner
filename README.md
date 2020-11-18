# WordCloudRunner

import java.io.IOException;
import java.net.MalformedURLException;
import java.net.URL;
import java.net.URLConnection;
import java.util.Scanner;

public class CloudRunner {

	public static void main(String[] args)
  
	{
		try {
			URL myURL = new URL("http://example.com/");
			//URL myURL = new URL("https://www.ctevans.net/Nvcc/HIS242/Notes/Rasputin.html");
			//URL myURL = new URL("http://www.script-o-rama.com/movie_scripts/a1/bee-movie-script-transcript-seinfeld.html");
			//URL myURL = new URL("http://unix.rulez.org/~calver/funny/LifeofBrian.html");
			//URL myURL = new URL("http://rouxacademy.com/");
			//URL myURL = new URL("https://myimmortal.fandom.com/wiki/My_Immortal/Chapters_1-11");
			//URL myURL = new URL("https://www.art-deco.nu/docs/33aa66-communist-manifesto-full-text-copy-and-paste");
			URLConnection site = myURL.openConnection();
			site.connect();
			Scanner reader = new Scanner( site.getInputStream() );
			String str=reader.useDelimiter( "\\Z" ).next();
			 
			Cloud word = new Cloud();
			
			word.populateLists(str);
			
			word.makeMap();
			
			word.paint();
		}
		catch (MalformedURLException e) {
			// new URL() failed
			// ...
		}
		catch (IOException e) {
			// openConnection() failed
			// ...
		}
	}
}
