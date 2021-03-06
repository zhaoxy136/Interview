### Description
[65H](https://leetcode.com/problems/valid-number/description/)

### Solution
//Version 0: 

    class Solution {
    public boolean isNumber(String s) {
        // +/- must occur in the beginning or right after e
        // e have to follow some number and have to followed be some number
        //at most one e/. in the string
        //no white spaces
        
        s = s.trim();
        if (s.length() == 0) return false;
        char[] str = s.toCharArray();
        
        boolean expo = false;
        boolean dot = false;
        boolean numBefExpo = false;
        boolean numAfterExpo = false;
        boolean numBefDot = false;
        boolean numAfterDot = false;
        
        for (int i = 0; i < str.length; i++) {
            if (str[i] == '+' || str[i] == '-') {
                if (i != 0 && str[i-1] != 'e') return false;
            } else if (str[i] == 'e') {
                if (expo) return false;
                expo = true;
            } else if (str[i] == '.') {
                if (expo || dot) return false;
                dot = true;
            } else if (Character.isDigit(str[i])) {
                if (expo) {
                    numAfterExpo = true;
                } else {
                    numBefExpo = true;
                }
                if (dot) {
                    numAfterDot = true;
                } else {
                    numBefDot = true;
                }
            } else {
                return false;
            }
        }
        if (expo && (!numBefExpo || !numAfterExpo)) return false;
        if (dot && !numBefDot && !numAfterDot) return false;
        return true;
    }
    }

//Version 1:

    public boolean isNumber(String s) {
    s = s.trim();
    
    boolean pointSeen = false;
    boolean eSeen = false;
    boolean numberSeen = false;
    boolean numberAfterE = true;
    for(int i=0; i<s.length(); i++) {
        if('0' <= s.charAt(i) && s.charAt(i) <= '9') {
            numberSeen = true;
            numberAfterE = true;
        } else if(s.charAt(i) == '.') {
            if(eSeen || pointSeen) {
                return false;
            }
            pointSeen = true;
        } else if(s.charAt(i) == 'e') {
            if(eSeen || !numberSeen) {
                return false;
            }
            numberAfterE = false;
            eSeen = true;
        } else if(s.charAt(i) == '-' || s.charAt(i) == '+') {
            if(i != 0 && s.charAt(i-1) != 'e') {
                return false;
            }
        } else {
            return false;
        }
    }
    
    return numberSeen && numberAfterE;
    }

