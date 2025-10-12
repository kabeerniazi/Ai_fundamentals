# 🏆 Module 7 Notes: Best Practices for Model Development

Building a model is one thing; building a *good* model is another. This module is about the art and science of model development. How do you evaluate your model's performance, and how do you diagnose and fix common problems?

## 1. Evaluating Your Model: Beyond the Training Set

So far, we've only judged our model based on how well it fits the data we used to train it. This is a critical mistake.

* **The Analogy:** It's like letting a student write their own final exam questions. They'll get a perfect score, but it tells you nothing about whether they've actually learned the material.

To get a true measure of your model's ability to generalize to new, unseen data, you must split your data.

* **The Standard Split:**
    1.  **Training Set (e.g., 60%):** This is the data the model learns from. It's the "practice exam."
    2.  **Cross-Validation (CV) Set (e.g., 20%):** Also called the "validation" or "dev" set. You use this set to tune your model's parameters (like the regularization parameter λ or the degree of polynomial features). It's like a "midterm exam" to check your progress.
    3.  **Test Set (e.g., 20%):** You only touch this set **once**, at the very end, to get a final, unbiased report on your model's performance. This is the "final exam."

By evaluating your model on a separate test set, you get a much more realistic estimate of how it will perform in the real world.

---

## 2. Diagnosing Problems: Bias vs. Variance

Your model isn't performing well. What do you do? The first step is to diagnose the problem. The two most common issues are **high bias** and **high variance**.

* **High Bias (Underfitting):**
    * **The Symptom:** Your model is too simple. It performs poorly on the **training set** and also performs poorly on the **cross-validation set**.
    * **The Analogy:** You brought a toy hammer to a construction job. It's just not powerful enough to do the work. It fails to capture the basic pattern in the data.

* **High Variance (Overfitting):**
    * **The Symptom:** Your model is too complex. It does great on the **training set** (low cost), but it performs terribly on the **cross-validation set** (high cost). There's a huge gap between the training error and the validation error.
    * **The Analogy:** You've created a custom-tailored suit that fits one person perfectly but is completely useless for anyone else. Your model has memorized the training data instead of learning the general pattern.

### How to Fix the Problem

Once you know whether you have a bias or variance problem, you can choose the right strategy. Wasting time on the wrong fix is one of the biggest productivity drains in machine learning.

* **If you have HIGH BIAS (Underfitting):**
    * **Get more features.** Your model needs more information.
    * **Add polynomial features** ($x^2, x^3$, etc.). Make your model more complex.
    * **Decrease the regularization parameter (λ).** Let your model fit the data more closely.

* **If you have HIGH VARIANCE (Overfitting):**
    * **Get more training examples.** A model finds it harder to memorize the data if there's more of it.
    * **Try a smaller set of features.** Simplify your model.
    * **Increase the regularization parameter (λ).** Penalize complexity and force your model to be simpler.

### Key Takeaways for Module 7

1.  **Split Your Data:** Never evaluate your model on the same data you trained it on. Use a train/validation/test split.
2.  **Diagnose Before You Act:** Determine if your problem is high bias or high variance by comparing training error to validation error.
3.  **Choose the Right Tool for the Job:** Apply targeted fixes based on your diagnosis. Don't waste weeks collecting more data if your problem is actually high bias!