import java.util.Stack;

public class BracketValidator {
    
    public static boolean isValid(String s) {
        Stack<Character> stack = new Stack<>();
        
        for (char bracket : s.toCharArray()) {
            if (bracket == '(' || bracket == '[' || bracket == '{') {
                stack.push(bracket);
            } else if (bracket == ')' || bracket == ']' || bracket == '}') {
                if (stack.isEmpty()) {
                    return false; 
                }
                
                char top = stack.pop();
                if ((bracket == ')' && top != '(') ||
                    (bracket == ']' && top != '[') ||
                    (bracket == '}' && top != '{')) {
                    return false; 
                }
            }
        }
        
        return stack.isEmpty();
    }
    
    public static void main(String[] args) {
        String[] tests = {"()", "(()()((())))", "(((())()", "{[()]}", "{[()]}("};
        
        for (String test : tests) {
            System.out.println(test + " -> " + isValid(test));
        }
    }
}
