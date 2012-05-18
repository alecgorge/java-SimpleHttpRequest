java-SimpleHttpRequest
======================

A simple set of classes for making HTTP requests around `HttpURLConnection`. Nothing fancy, just GET, POST, HEAD, PUT and DELETE. The API is chainable.

There is no real documentation, but every method is very plainly named and follows fairly standard Java conventions. 

A quick example:

	import com.alecgorge.java.http.HttpRequest;

	class Test {
		public static void main(String[] args) {
			HttpRequest r = new HttpRequest(new URL("http://example.com/post.php"));
			r.addGetValue("key", "value")
			 .setHeader("custom-header", "value")
			 .addPostValue("arr[]", "a")
			 .addPostValue("arr[]", "b");

			HttpResponse response = r.post();

			if(response.hasHeader("Location")) {
				System.out.println("Location: " + response.getHeader("Location"));
			}
			
			// also you could use getInputStream, getReader, or getInputStreamReader
			System.out.println("\n\n" + response.getResponse()); 
		}
	}