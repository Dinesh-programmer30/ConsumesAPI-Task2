# ConsumesAPI-Task2
import java.io.BufferedReader;
import java.io.InputStreamReader;
import java.net.HttpURLConnection;
import java.net.URL;

public class ConsumesAPI {

    public static void main(String[] args) {
        try {
            // Step 1: API URL
            URL url = new URL("https://jsonplaceholder.typicode.com/posts/1");

            // Step 2: HTTP Connection (NOT database connection)
            HttpURLConnection con = (HttpURLConnection) url.openConnection();

            // Step 3: Request method
            con.setRequestMethod("GET");

            // Step 4: Read response
            BufferedReader br = new BufferedReader(
                    new InputStreamReader(con.getInputStream()));

            String line;
            StringBuilder response = new StringBuilder();

            while ((line = br.readLine()) != null) {
                response.append(line);
            }

            br.close();

            // Step 5: Display output
            System.out.println(response.toString());

        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}