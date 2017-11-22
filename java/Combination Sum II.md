```java
public class Solution {
    public List<List<Integer>> combinationSum2(int[] candidates, int target) {
        List<List<Integer>> res = new LinkedList<>();
        if(candidates == null || candidates.length < 1)
            return res;
        Arrays.sort(candidates);
        backtrack(res, new LinkedList<Integer>(), candidates, target, 0);
        return res;
    }
    
    private void backtrack(List<List<Integer>> res, List<Integer> list, int[] candidates, int target, int start) {
        if(target == 0)
            res.add(new LinkedList<>(list));
        else if(target > 0) {
            for(int i = start; i < candidates.length && target >= candidates[i]; i++) {
                if(i == start || candidates[i] != candidates[i - 1]) {
                    list.add(candidates[i]);
                    backtrack(res, list, candidates, target - candidates[i], i + 1);
                    list.remove(list.size() - 1);
                }
            }
        }
    }
}
```
