import java.util.Scanner;
import java.util.regex.Matcher;
import java.util.regex.Pattern;

public class AIChatbot {
    
    private static final String[][] patterns = {
        {"hi|hello|hey there", "Hello!", "Hey!", "Hi there!"},
        {"how are you?", "I am doing well, thank you!", "I am fine, thank you!"},
        {"what is your name?", "I am a chatbot.", "You can call me a chatbot."},
        {"I love u?", "I am also love you.", "But i am a virtual machine."},
        
        {"I want to make an Appointment", "Sure, Which city?"},
        {"two plus two", "four"},
        {"you make my friend?", "Sure!"},
        {"what is capital of India", "New Delhi"},
        {"31 may", "Your booking is confirmed"},
        {"Thanks", "You are Welcome"},
        {"quit", "Bye! Take care."}
    };

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        System.out.println("Welcome to the Java Chatbot. Type 'quit' to exit.");
        
        while (true) {
            System.out.print("You: ");
            String userInput = 
            scanner.nextLine();
            
            String response = respond(userInput);
            System.out.println("Chatbot: " + response);
            
            if (userInput.equalsIgnoreCase("quit")) {
                break;
            }
        }
        
        scanner.close();
    }
    
    private static String respond(String input) {
        for (String[] pattern : patterns) {
            Pattern r = Pattern.compile(pattern[0], Pattern.CASE_INSENSITIVE);
            Matcher m = r.matcher(input);
            if (m.find()) {
                return pattern[(int) (Math.random() * (pattern.length - 1)) + 1];
            }
        }
        return "I don't understand.";
    }
}
