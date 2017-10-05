Description:
[Determine if a graph is Bipartite Graph](https://en.wikipedia.org/wiki/Bipartite_graph)

Solution:

    public class BiGraph {
    public static boolean isBigraph(int n, int[][] edges) {
        int[] set = new int[n];
        Map<Integer, List<Integer>> map = new HashMap<>();
        for (int i = 0; i < n; i++) {
            map.put(i, new ArrayList<>());
        }
        for (int[] edge : edges) {
            map.get(edge[0]).add(edge[1]);
            map.get(edge[1]).add(edge[0]);
        }
        for (int key : map.keySet()) {
            if (set[key] == 0) {
                set[key] = 1;
                if (!helper(key, set, map)) return false;
            }
        }
        return true;
    }

    public static boolean helper(int key, int[] set, Map<Integer, List<Integer>> map) {
        for (int adj : map.get(key)) {
            if (set[adj] == 0) {
                set[adj] = 2 / set[key];
                if (!helper(adj, set, map)) return false;
            } else if (set[key] * set[adj] != 2) {
                return false;
            }
        }
        return true;
    }
    }
    
    
