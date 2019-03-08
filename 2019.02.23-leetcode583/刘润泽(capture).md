```java
    public int minDistance(String word1, String word2) {
        int m = word1.length()+1;
        int n = word2.length()+1;

        int[][] bp = new int[m][n];

        for (int i=0; i<m; i++){
            bp[i][0] = i;
        }
        for (int i=0; i<n; i++){
            bp[0][i] = i;
        }

        for (int i=1;i<m;i++) {
            for (int j=1;j<n;j++) {
                if (word1.charAt(i-1)==word2.charAt(j-1)){
                    bp[i][j] = bp[i-1][j-1];
                } else {
                    bp[i][j] = 1+Math.min(bp[i][j-1],bp[i-1][j]);
                }
            }
        }

        return bp[m-1][n-1];
    }
```
