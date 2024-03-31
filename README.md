# Home-assignment
import java.util.Random; class TreeNode {
int val;
TreeNode left, right;

public TreeNode(int val) { this.val = val;
left = right = null;
}
}
 
class BinarySearchTree { TreeNode root;

public void insert(int val) { root = insertRec(root, val);
}

private TreeNode insertRec(TreeNode root, int val) { if (root == null) {
root = new TreeNode(val); return root;
}

if (val < root.val) {
root.left = insertRec(root.left, val);
} else if (val > root.val) {
root.right = insertRec(root.right, val);
}

return root;
}

public int getMinLeafLevel() { return getMinLeafLevel(root);
}

private int getMinLeafLevel(TreeNode root) { if (root == null)
return Integer.MAX_VALUE;

if (root.left == null && root.right == null) return 0;

return Math.min(getMinLeafLevel(root.left), getMinLeafLevel(root.right)) +
1;
}

public int getMaxLeafLevel() { return getMaxLeafLevel(root);
}

private int getMaxLeafLevel(TreeNode root) { if (root == null)
return Integer.MIN_VALUE;
 
if (root.left == null && root.right == null) return 0;

return Math.max(getMaxLeafLevel(root.left), getMaxLeafLevel(root.right)) +
1;
}
}

public class LeafLevelDiﬀerence { public static void main(String[] args) {
int[] leafLevelDiﬀerenceCount = new int[101]; // to store counts of diﬀerences

for (int i = 0; i < 50; i++) { // repeat 50 times BinarySearchTree bst = new BinarySearchTree(); Random rand = new Random();

for (int j = 0; j < 100; j++) { // generate 100 random numbers
int randomNumber = rand.nextInt(1000); // assuming numbers from 0 to
999
bst.insert(randomNumber);
}

int minLeafLevel = bst.getMinLeafLevel(); int maxLeafLevel = bst.getMaxLeafLevel();
int diﬀerence = Math.abs(maxLeafLevel - minLeafLevel); leafLevelDiﬀerenceCount[diﬀerence]++;
System.out.println("Run " + (i + 1) + ": Minimum Leaf Level = " + minLeafLevel + ", Maximum Leaf Level = " + maxLeafLevel);
}

System.out.println("\nLeaf Level Diﬀerence Counts:"); for (int i = 0; i <= 100; i++) {
if (leafLevelDiﬀerenceCount[i] != 0) { System.out.println("Diﬀerence of " + i + " occurred " +
leafLevelDiﬀerenceCount[i] + " times.");
}
}
}
}
 

