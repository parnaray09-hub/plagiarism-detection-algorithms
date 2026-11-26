# Plagiarism Detection Studio
### Comparative Study of String Matching Algorithm Efficiency & Performance Analysis

A web-based Plagiarism Detection System built for **Capstone Project 6**. This interactive application detects text similarities between two documents and compares the performance of three classic string matching algorithms: **Naïve Pattern Matching**, **Rabin-Karp**, and **Knuth-Morris-Pratt (KMP)**.

---

## Problem Statement
Develop a plagiarism detection system that identifies matching words or patterns between two text documents by implementing Naïve Pattern Matching, Rabin-Karp, and KMP algorithms, and compare their performance based on execution time, character comparisons, pattern length, and document size.

---

## Key Features
- **Document-to-Document Plagiarism Check:** Automatically splits the source document into overlapping word phrases (N-Grams, configurable from 3 to 6 words) and searches for them in the suspect document.
- **Exact Pattern Search Mode:** Allows searching for any specific substring (including repetitive worst-case patterns like `AAA...B`).
- **Visual Plagiarism Highlighter:** Highlights all matched segments in the suspect document and calculates the overall similarity percentage.
- **Live Performance Metrics:** Measures real-time execution time (in milliseconds using `performance.now()`) and exact character comparisons for all three algorithms side-by-side.
- **Interactive Scaling Benchmark:** Tests document sizes from 5,000 to 50,000 characters across Normal Text and Worst-Case Repetitive Text with interactive Chart.js graphs.
- **Zero Setup Required:** Built as a single-file web application using HTML, Tailwind CSS, and Chart.js.

---

## How the 3 Algorithms Work (Quick Viva Guide)

### 1. Naïve Pattern Matching
- **How it works:** Slides the pattern over the text one character at a time and checks every character from left to right. If a mismatch occurs, it shifts by 1 position and starts checking again from the beginning of the pattern.
- **Pros:** Very simple to implement; requires no preprocessing or extra memory.
- **Cons:** Slow on repetitive text because it re-checks characters it has already matched.

### 2. Rabin-Karp Algorithm
- **How it works:** Uses a **rolling hash function** to convert the pattern and each text window of length `m` into a numeric hash value. It only compares characters one-by-one when the hash values match.
- **Pros:** Very efficient for multi-pattern plagiarism detection (checking many phrases at once).
- **Cons:** Hash collisions (spurious hits) can degrade worst-case performance to `O(n * m)`.

### 3. Knuth-Morris-Pratt (KMP) Algorithm
- **How it works:** Precomputes an **LPS (Longest Proper Prefix which is also Suffix)** array for the pattern. When a mismatch happens, it uses the LPS array to skip redundant comparisons so the main text pointer never moves backward.
- **Pros:** Guaranteed linear time `O(n + m)` even in the worst case (repetitive text).
- **Cons:** Requires `O(m)` extra space and preprocessing time to build the LPS table.

---

## Time & Space Complexity Comparison

| Algorithm | Preprocessing | Best Case | Average Case | Worst Case | Space Complexity |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **Naïve Matching** | `O(1)` | `O(n)` | `O(n + m)` | `O(n * m)` | `O(1)` |
| **Rabin-Karp** | `O(m)` | `O(n + m)` | `O(n + m)` | `O(n * m)` | `O(1)` |
| **KMP Algorithm** | `O(m)` | `O(n + m)` | `O(n + m)` | `O(n + m)` | `O(m)` |

*(Where `n` = length of the document/text, and `m` = length of the pattern.)*

---

## How to Run
1. Download or clone this repository.
2. Open `index.html` in any modern web browser (Chrome, Edge, Firefox).
3. Use the **Plagiarism Analyzer** tab to compare documents, or switch to the **Benchmark & Complexity** tab to run scaling graphs.
