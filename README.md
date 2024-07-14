import java.util.ArrayList;
import java.util.Collections;
import java.util.List;
import java.util.Scanner;
public class Main {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        String input = scanner.nextLine();
        List<String> result = new ArrayList<>();
        generatePermutations("", input, input, result);
        Collections.sort(result);
        for (String str : result) {
            System.out.println(str);
        }
    }
    private static void generatePermutations(String prefix, String remaining, String original, List<String> result) {
        int n = remaining.length();
        if (n == 0) {
            if (prefix.compareTo(original) > 0) {
                result.add(prefix);
            }
        } else {
            for (int i = 0; i < n; i++) {
                generatePermutations(prefix + remaining.charAt(i), 
                                     remaining.substring(0, i) + remaining.substring(i + 1), 
                                     original, 
                                     result);
            }
        }
    }
}
