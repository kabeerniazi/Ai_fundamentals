# 📊 Module 3 Notes: Linear Regression with Multiple Variables

In the real world, a single feature is rarely enough to make an accurate prediction. A house's price doesn't just depend on its size; it also depends on the number of bedrooms, the number of floors, and its age. It's time to upgrade our model to handle multiple features at once.

## 1. The Model: Upgrading to Vectors

Our model's goal is the same, but the formula gets a promotion. Instead of a single weight `w`, we now have a **vector of weights** $\mathbf{w}$, where each weight corresponds to a different feature.

* **The Old Formula (One Feature):** $f_{w,b}(x) = wx + b$
* **The New Formula (Multiple Features):** $f_{\mathbf{w},b}(\mathbf{x}) = w_0x_0 + w_1x_1 + \dots + w_{n-1}x_{n-1} + b$

This looks complicated to write out. We can simplify it dramatically using the **dot product** we learned in Module 1.

* **The Vectorized Formula:** $f_{\mathbf{w},b}(\mathbf{x}) = \mathbf{w} \cdot \mathbf{x} + b$

* **The Components:**
    * $\mathbf{x}$: A **vector** representing the features of a single example (e.g., `[2104, 5, 1, 45]`).
    * $\mathbf{w}$: A **vector** of weights, one for each feature (e.g., `[w_0, w_1, w_2, w_3]`).
    * `b`: The **bias**, which is still a single number.
    * $\mathbf{w} \cdot \mathbf{x}$: The dot product of the weights and features. This is the **weighted sum** of the features and is the heart of the prediction.

The Cost Function and Gradient Descent still work exactly the same way conceptually—we're still trying to minimize the Mean Squared Error by walking downhill. The only difference is that now we're walking in a higher-dimensional space, adjusting multiple `w`'s at once.

## 2. The Problem: Unbalanced Features and the Need for Feature Scaling

When you have multiple features, you often run into a big problem: **the scales are wildly different.**

* **Feature 1:** House size (e.g., 800 to 4000 sqft)
* **Feature 2:** Number of bedrooms (e.g., 1 to 5)

The "size" feature has a range of thousands, while "bedrooms" has a range of just a few. This creates a big issue for Gradient Descent.

* **The Analogy:** Imagine you're trying to find the lowest point in a long, narrow, steep-sided canyon. Because the canyon is so stretched out in one direction, Gradient Descent will tend to bounce back and forth between the steep walls instead of making steady progress down the length of the canyon. It will eventually find the bottom, but it will take a painfully long time.



This is what happens when your features are on different scales. The cost function becomes a stretched-out "canyon," and the algorithm struggles to converge.

* **The Solution: Feature Scaling.** We rescale our features so they all have a similar range. This transforms the narrow canyon into a nice, symmetrical "bowl," allowing Gradient Descent to march straight to the bottom quickly and efficiently.



* **The Method (Z-score Normalization):** For each feature, we subtract its mean and then divide by its standard deviation.
    $x_j := \frac{x_j - \mu_j}{\sigma_j}$
    After this process, every feature will have a mean of approximately 0 and a standard deviation of 1.

## 3. Feature Engineering: Creating New Features from Old Ones

What if the relationship isn't a straight line? For example, maybe house prices increase with size, but only up to a point, after which the relationship flattens out.

**Feature Engineering** is the art of creating new, more powerful features from your existing data.

* **Polynomial Regression:** The most common form of feature engineering is to create polynomial features. If you have a feature `x` (house size), you can create new features like `x²` (size squared) and `x³` (size cubed).

Your model then becomes:
$f_{\mathbf{w},b}(\mathbf{x}) = w_1x + w_2x^2 + w_3x^3 + b$

Even though this model can fit a complex curve, notice something amazing: **it's still a linear model!** From the algorithm's perspective, `x`, `x²`, and `x³` are just three independent features. We can still use the exact same Gradient Descent algorithm to find the best `w`'s and `b`. This is an incredibly powerful idea.

### Key Takeaways for Module 3

1.  **Vectorization is King:** The dot product allows us to handle multiple features with clean, efficient code.
2.  **Scale Your Features:** Always use feature scaling (like Z-score normalization) when your input features have different ranges. This is one of the most important steps for making Gradient Descent work well.
3.  **Create Better Features:** Use feature engineering and polynomial regression to allow your linear model to fit complex, non-linear patterns.