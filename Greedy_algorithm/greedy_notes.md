
---

# 📌 Greedy Algorithm – Complete Notes

---

## 🔹 What is a Greedy Algorithm?

A **Greedy Algorithm** is an approach that makes the **locally optimal choice at each step** with the hope that these local choices lead to a **globally optimal solution**.

> ✔ “Take the best option available right now, without thinking about future consequences.”

---

## 🔹 Key Characteristics

* Makes decision **step by step**
* Chooses **best immediate result**
* Does **not backtrack**
* Simple and efficient
* May not always produce optimal solution

---

## 🔹 When Does Greedy Work?

A greedy algorithm works **only if** the problem satisfies:

### 1️⃣ Greedy Choice Property

A global optimum can be reached by choosing a local optimum.

### 2️⃣ Optimal Substructure

An optimal solution contains optimal solutions to its subproblems.

---

## 🔹 General Greedy Algorithm Template

```text
1. Sort / prioritize input if needed
2. Initialize result
3. Repeat:
   - Pick the best available option
   - Update result
4. Return result
```

---

## 🔹 Types of Greedy Strategies

| Strategy        | Example             |
| --------------- | ------------------- |
| Smallest first  | Huffman Coding      |
| Largest first   | Fractional Knapsack |
| Earliest finish | Activity Selection  |
| Maximum profit  | Job Scheduling      |
| Two pointers    | Bag of Tokens       |
| Min / Max heap  | Meeting Rooms       |

---

## 🔹 Common Greedy Problems (Must Know)

| Problem             | Greedy Strategy      |
| ------------------- | -------------------- |
| Activity Selection  | Earliest finish time |
| Fractional Knapsack | Max value/weight     |
| Huffman Encoding    | Min frequency        |
| Minimum Coins       | Largest denomination |
| Gas Station         | Track surplus        |
| Bag of Tokens       | Min cost / Max gain  |
| Jump Game           | Farthest reach       |

---

## 🔹 Example (Bag of Tokens)

```java
if (power >= tokens[i]) {
    power -= tokens[i];
    score++;
} else if (score >= 1) {
    score--;
    power += tokens[j];
}
```

👉 Choose **minimum cost** or **maximum gain** at each step.

---

## 🔹 Greedy vs Dynamic Programming

| Greedy             | DP              |
| ------------------ | --------------- |
| Fast & simple      | Slower          |
| Local decision     | Global decision |
| No memoization     | Uses memo/table |
| Not always optimal | Always optimal  |

---

## 🔹 How to Identify a Greedy Problem?

Ask yourself:

* Can I make a decision now without worrying about future?
* Is sorting helpful?
* Is there a clear “best choice”?
* Can local optimal lead to global optimal?

✔ If YES → Greedy may work

---

## 🔹 Greedy Algorithm Pitfalls

❌ Greedy does NOT work for:

* 0/1 Knapsack
* Longest Increasing Subsequence
* Coin change (in some cases)

---

## 🔹 Advantages

✔ Easy to implement
✔ Very fast
✔ Low memory usage

---

## 🔹 Disadvantages

❌ May give wrong answer
❌ Problem-specific
❌ Hard to prove correctness

---

## 🔹 Greedy Proof Techniques

* Exchange Argument
* Cut Property
* Stay Ahead Argument

---

## 🔹 One-Line Exam Definition

> **A Greedy Algorithm is an algorithmic strategy that makes the locally optimal choice at each step to find a global optimum.**

---

