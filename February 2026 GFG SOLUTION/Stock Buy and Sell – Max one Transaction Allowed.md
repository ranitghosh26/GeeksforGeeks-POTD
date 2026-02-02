# Stock Buy and Sell – Java Solution

The following code uses a single pass to track the minimum buying price and the maximum profit achievable.

```java
class Solution {
    public int maxProfit(int[] prices) {
        // If there are no prices or only one day, no profit can be made
        if (prices == null || prices.length < 2) {
            return 0;
        }

        // Initialize minPrice to the first day's price
        int minPrice = prices[0];
        int maxProfit = 0;

        // Iterate through the array starting from the second day
        for (int i = 1; i < prices.length; i++) {
            
            // 1. If we find a price lower than our current minPrice, update it
            if (prices[i] < minPrice) {
                minPrice = prices[i];
            } 
            // 2. Otherwise, check if selling today gives us a better profit
            else {
                int currentProfit = prices[i] - minPrice;
                if (currentProfit > maxProfit) {
                    maxProfit = currentProfit;
                }
            }
        }

        return maxProfit;
    }

    public static void main(String[] args) {
        Solution sol = new Solution();
        
        int[] example1 = {7, 10, 1, 3, 6, 9, 2};
        System.out.println("Max Profit: " + sol.maxProfit(example1)); // Output: 8
        
        int[] example2 = {7, 6, 4, 3, 1};
        System.out.println("Max Profit: " + sol.maxProfit(example2)); // Output: 0
    }
}
