# stream-and-file-example
import java.io.BufferedReader;
import java.io.BufferedWriter;
import java.io.FileReader;
import java.io.FileWriter;
import java.io.IOException;
import java.util.List;
import java.util.stream.Collectors;
public class StreamAndFileExample {
public static void main(String[] args) {

String inputFilePath = &quot;input_numbers.txt&quot;;
String outputFilePath = &quot;output_squares.txt&quot;;
try {

List&lt;Integer&gt; numbers = readNumbersFromFile(inputFilePath);

List&lt;Integer&gt; squares = numbers.stream()
.map(num -&gt; num * num)
.collect(Collectors.toList());

writeSquaresToFile(outputFilePath, squares);
System.out.println(&quot;Squares written to &quot; + outputFilePath);
} catch (IOException e) {

e.printStackTrace();
}
}

private static List&lt;Integer&gt; readNumbersFromFile(String filePath) throws
IOException {
try (BufferedReader reader = new BufferedReader(new FileReader(filePath))) {
return reader.lines()
.map(Integer::parseInt)
.collect(Collectors.toList());
}
}

private static void writeSquaresToFile(String filePath, List&lt;Integer&gt; squares) throws
IOException {
try (BufferedWriter writer = new BufferedWriter(new FileWriter(filePath))) {
for (Integer square : squares) {
writer.write(square.toString());
writer.newLine();
}
}
}
}
Output
Squares written to output_squares.txt
1
4
9
16
25
