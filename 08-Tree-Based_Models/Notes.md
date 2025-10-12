# 🌳 Module 8 Notes: Tree-Based Models

So far, all our models have been based on mathematical equations (lines, curves, etc.). Now we'll explore a completely different approach that's intuitive, powerful, and very popular: **Decision Trees**.

## 1. The Decision Tree: Asking a Series of Questions

A decision tree makes predictions by asking a series of yes/no questions about the features.

* **The Analogy:** It works just like the game "20 Questions." You start with a broad question and, based on the answer, ask a more specific follow-up question until you've narrowed down the possibilities and can make a final guess.



* **How it Works:**
    1.  **Root Node:** The tree starts at the top with a single node that considers the entire dataset. It searches for the single best feature and threshold that splits the data into two groups that are as "pure" as possible (i.e., mostly containing one class).
    2.  **Splitting:** It splits the data based on this question (e.g., "Is `age` < 30?").
    3.  **Child Nodes:** It repeats the process for each of the new nodes, finding the best question to ask for that subset of the data.
    4.  **Leaf Nodes:** It continues splitting until it reaches a stopping criterion (e.g., the node is perfectly pure, or the tree has reached a maximum depth). The final nodes are called **leaf nodes**, and they provide the prediction.

## 2. The Power of Ensembles: Forests and Boosting

A single decision tree is easy to understand, but it has a major weakness: it's prone to **overfitting**. A deep tree can create a unique path for every single example in the training data, essentially memorizing it.

The solution is not to use just one tree, but a whole **forest** of them. This is called an **ensemble method**.

* **The Analogy:** If you ask one person for their opinion, it might be biased. If you ask a thousand people and average their opinions, you'll get a much wiser and more robust answer.

* **Random Forest:**
    * **How it works:** It builds many decision trees. For each tree, it takes a random sample of the training data and also considers only a random subset of features for each split. This ensures that all the trees are different from each other.
    * **Prediction:** To make a prediction, it gets a vote from every tree in the forest and goes with the majority. This process, called **bagging**, dramatically reduces overfitting and improves accuracy.

* **Gradient Boosted Trees (XGBoost):**
    * **How it works:** This is another, even more powerful ensemble method. Instead of building trees independently, it builds them **sequentially**.
    1.  It starts by building one simple tree that makes a basic prediction.
    2.  It looks at the errors (the "residuals") that the first tree made.
    3.  It then builds a **second tree** whose job is to **predict the errors** of the first tree.
    4.  It adds the prediction of the second tree to the first, correcting some of its mistakes.
    5.  It repeats this process, with each new tree learning to fix the remaining errors of the ensemble.
    * **Why it's powerful:** This method, called **boosting**, is often one of the highest-performing algorithms in classical machine learning competitions (i.e., for data that isn't images or text).

### Key Takeaways for Module 8

1.  **Decision Trees are like flowcharts** that make predictions by asking a series of simple questions.
2.  **Ensemble Methods are Powerful:** Combining the predictions of many models (especially trees) is a highly effective strategy for improving accuracy and reducing overfitting.
3.  **Random Forests** build many independent trees and average their votes.
4.  **Gradient Boosted Trees** build trees sequentially, with each new tree learning from the mistakes of the previous ones.