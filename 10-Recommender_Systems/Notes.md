# 🍿 Module 10 Notes: Recommender Systems

Welcome to the final and one of the most impactful topics in this course: **Recommender Systems**. These are the algorithms that power product recommendations on Amazon, movie suggestions on Netflix, and song choices on Spotify.

## 1. Collaborative Filtering: "Users who liked this also liked..."

This is the most common approach to building recommender systems.

* **The Core Idea:** It relies on the "wisdom of the crowd." It doesn't need to know anything about the items themselves (movies, products, etc.). It only needs a matrix of **user ratings**.
* **The Analogy:** You ask your friend for a movie recommendation. You trust their suggestion because they have similar tastes to you. Collaborative filtering automates this process for millions of users.

* **How it Works:**
    1.  **Learning Features:** The algorithm simultaneously learns two sets of vectors from the user-item rating matrix:
        * A **parameter vector ($\theta$) for each user**, which represents their tastes.
        * A **feature vector ($x$) for each item**, which represents its characteristics.
    2.  **The Magic:** The algorithm learns these features in such a way that the dot product of a user's vector and an item's vector ($\theta^{(j)} \cdot x^{(i)}$) will approximate the rating that user `j` would give to item `i`.
    3.  **Making Recommendations:** To recommend items for a user, we simply calculate the dot product of their user vector with the vectors of all the items they haven't seen yet. The items with the highest predicted ratings are our top recommendations.



---

## 2. Content-Based Filtering: "Because you liked an item with these features..."

This approach uses the features of the **items themselves** to make recommendations.

* **The Core Idea:** If you like a movie with certain features (e.g., genre=sci-fi, director=Christopher Nolan, actor=Leonardo DiCaprio), the system will recommend other movies with similar features.
* **The Analogy:** A music expert recommends a new band to you. They say, "Because you like Led Zeppelin's heavy guitar riffs and blues-inspired vocals, you might also like Greta Van Fleet."

* **How it Works:**
    1.  **Item Features:** For each item, we need a feature vector ($x$) that describes its properties. For a movie, this could be `[sci-fi, action, thriller, romance, ...]` where the values are 1 or 0.
    2.  **Learning User Preferences:** For each user, we learn a parameter vector ($\theta$) that represents how much they like each of those features. This is essentially a **linear regression problem for each user**.
    3.  **Making Recommendations:** The predicted rating for a user and a new item is, once again, the dot product $\theta \cdot x$. We recommend the items with the highest predicted scores.

### Collaborative vs. Content-Based

| Feature | Collaborative Filtering | Content-Based Filtering |
| :--- | :--- | :--- |
| **Data Needed** | User-item interaction matrix (ratings) | Features of the items themselves |
| **Pros** | Can find surprising, "serendipitous" connections. | Works for new items with no ratings. |
| **Cons** | Struggles with new users/items ("cold start problem"). | Can only recommend items similar to what the user already likes. |

### Key Takeaways for Module 10

1.  **Recommender Systems** are a powerful application of machine learning that drives user engagement on many platforms.
2.  **Collaborative Filtering** leverages user behavior to make recommendations based on similar tastes.
3.  **Content-Based Filtering** uses the inherent features of items to recommend similar items.
4.  At the heart of both methods is the **dot product**, which is used to predict a user's likely rating for an item.

***

**Congratulations, Kabeer!** That covers the notes for all the modules. You now have a complete blueprint for the text-based content of your entire course.