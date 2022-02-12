class Solution {
public:
	TreeNode* mergeTree(TreeNode* t1, TreeNode* t2) {
		if (!t1 && !t2)
			return NULL;
		if (!t1)
			return t2;
		if (!t2)
			return t1;
		
		merge(t1, t2);
		return t1;
	}
	
	void merge(TreeNode* t1, TreeNode* t2) {
		t1->val += t2->val;
		
		// merge left
		if (t1->left && t2->left) merge(t1->left, t2->left);  // both t1, t2 have left child
		else if (t2->left) t1->left = t2->left;  // only t2 has left child

		// merge right
		if (t1->right && t2->right) merge(t1->right, t2->right);
		else if (t2->right) t1->right = t2->right;
	}
};


