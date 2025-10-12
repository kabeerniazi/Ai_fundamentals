# 📈 Module 2 Notes: Linear Regression with One Variable

Welcome to your first real machine learning model! Linear Regression is a fundamental algorithm and the perfect place to start. The goal is simple: **draw the best possible straight line through a set of data points.**

Think of predicting house prices. As the size of a house increases, its price generally increases. We're going to teach the machine how to find the exact line that describes this relationship.

## 1. The Model: Describing the Line

First, we need a mathematical way to represent a line. You might remember this from algebra class.

* **The Formula:** $f_{w,b}(x) = wx + b$

This is our **model**. It's a function that takes an input feature `x` and predicts an output.

* **The Components:**
    * `x`: The **input feature** (e.g., the size of a house in square feet).
    * `f_{w,b}(x)`: The **prediction** (e.g., the predicted price of the house).
    * `w` and `b`: These are the **parameters** of our model. They are the "knobs" we need to tune to make our line fit the data perfectly.
        * `w` is the **weight**. It controls the slope of the line. A larger `w` means the price goes up more steeply as the house size increases.
        * `b` is the **bias** (or y-intercept). It's the starting value. You can think of it as the base price of a house, even if its size was zero.

## 2. The Goal: Measuring "Best" with the Cost Function

How do we know if our line is a "good fit" for the data? We need a way to measure how wrong our predictions are. This is where the **Cost Function** comes in.

* **The Analogy:** Imagine playing darts. The "cost" is how far your dart is from the bullseye. A lower cost is better. Our goal is to get our model's predictions as close to the real data points as possible.

* **The Formula (Mean Squared Error):** $J(w,b) = \frac{1}{2m} \sum_{i=1}^{m} (f_{w,b}(x^{(i)}) - y^{(i)})^2$

Let's break that down:
1.  $(f_{w,b}(x^{(i)}) - y^{(i)})$: This is the **error** for a single data point. It's the difference between our prediction ($f_{w,b}(x^{(i)})$) and the actual value ($y^{(i)}$).
2.  $(...)^2$: We **square the error**. This does two things: it makes the error positive, and it punishes larger errors much more than smaller ones.
3.  $\sum$: We **sum up** all the squared errors for every one of our `m` training examples.
4.  $\frac{1}{2m}$: We take the **average**. This gives us a single number, the **cost**, that represents how wrong our model is on average. (The `2` is just a math trick that makes the calculus easier later on).

Our goal is to find the values of `w` and `b` that make this cost `J(w,b)` as small as possible.

## 3. The Method: Finding the Best `w` and `b` with Gradient Descent

So, how do we minimize the cost? We use an algorithm called **Gradient Descent**.

* **The Analogy:** Imagine you're standing on a foggy mountain and you want to get to the lowest point in the valley. You can't see the bottom, but you can feel which way is downhill from where you're standing. You take a small step in the steepest downhill direction, check again, and repeat. Eventually, you'll reach the bottom.

That's exactly what Gradient Descent does.
1.  It starts with some random values for `w` and `b`.
2.  It calculates the **gradient**—the "slope" of the cost function—which points in the direction of the steepest *increase* in cost.
3.  It takes a small step in the **opposite** direction (downhill).
4.  It repeats this process until it finds the bottom of the valley, which corresponds to the lowest possible cost.

* **The Update Rules:**
    * $w := w - \alpha \frac{\partial}{\partial w}J(w,b)$
    * $b := b - \alpha \frac{\partial}{\partial b}J(w,b)$

    Here, `α` (alpha) is the **learning rate**. It's a small number that controls how big of a step we take.
    * If `α` is too small, it will take forever to get to the bottom.
    * If `α` is too large, we might overshoot the bottom and end up on the other side of the valley, making our cost worse!

### Key Takeaways for Module 2

1.  **The Model:** A linear model is just a line defined by its weight `w` (slope) and bias `b` (intercept).
2.  **The Cost Function:** We measure the "goodness" of our model by calculating the Mean Squared Error between its predictions and the actual data.
3.  **Gradient Descent:** We find the best `w` and `b` by iteratively taking small steps "downhill" on the cost function until we find the minimum.