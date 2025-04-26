# DSA
Only top quality dsa material
#1.Question
Imagine you have n friends sitting in a circle, numbered 1 to n.

You are given a number k.
k tells you how many friends to count before someone gets eliminated.

How it works:
Start at Friend 1.

Count k friends, moving clockwise (like going around a clock).

Include the friend you start at as the first count.

The k-th friend you land on is eliminated (they leave the circle).

Start counting again from the friend right after the one who got eliminated.

Repeat steps 2–4 until only one friend is left.

That last friend is the winner!

Solution:
import java.util.*;

public class WinnerOfGame {
    public static int findTheWinner(int n, int k) {
        List<Integer> friends = new ArrayList<>();
        
        for (int i = 1; i <= n; i++) {
            friends.add(i);
        }
        
        int idx = 0;
        
        while (friends.size() > 1) {
            idx = (idx + k - 1) % friends.size();  // Find the k-th friend (circularly)
            friends.remove(idx);  // Eliminate that friend
        }
        
        return friends.get(0);  // The last remaining friend
    }

    public static void main(String[] args) {
        int n = 5, k = 2;
        System.out.println(findTheWinner(n, k));  // Output: 3

        n = 6;
        k = 5;
        System.out.println(findTheWinner(n, k));  // Output: 1
    }
}

