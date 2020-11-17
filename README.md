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
			//URL myURL = new URL("http://example.com/");
    			//URL myURL = new URL("https://www.ctevans.net/Nvcc/HIS242/Notes/Rasputin.html");
			//URL myURL = new URL("http://www.script-o-rama.com/movie_scripts/a1/bee-movie-script-transcript-seinfeld.html");
			URL myURL = new URL("http://unix.rulez.org/~calver/funny/LifeofBrian.html");
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
