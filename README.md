# Assignment 1 — Simulated Annealing: Exam Timetable Scheduling
## Observation Report

**Student Name  :** ___________________________  
**Student ID    :** ___________________________  
**Date Submitted:** ___________________________  

---

## How to Submit

1. Run each experiment following the instructions below
2. Fill in every answer box — do not leave placeholders
3. Make sure the `plots/` folder contains all required images
4. Commit this README and the `plots/` folder to your GitHub repo

---

## Before You Begin — Read the Code

Open `sa_timetable.py` and read through it. Then answer these questions.

**Q1. What does `count_clashes()` measure? What value means a perfect timetable?**

```
[ count_clashes() measures the number of conflicts in the timetable, such as two exams scheduled at the same time for students or overlapping constraints. It evaluates how bad the current timetable is. A value of 0 means a perfect timetable with no clashes. ]
```

**Q2. What does `generate_neighbor()` do? How is the new timetable different from the current one?**

```
[ generate_neighbor() creates a slightly modified version of the current timetable by making small random changes, such as swapping exam slots or reassigning times. The new timetable differs only in a few positions, allowing gradual improvement. This helps the algorithm explore nearby solutions.]
```

**Q3. In `run_sa()`, there is this line:**
```python
if delta < 0 or random.random() < math.exp(-delta / T):
```
**What does this line decide? Why does SA sometimes accept a worse solution?**

```
[ if delta < 0 or random.random() < math.exp(-delta / T):]
```

---

## Experiment 1 — Baseline Run

**Instructions:** Run the program without changing anything.
```bash
python sa_timetable.py
```

**Fill in this table:**

| Metric | Your result |
|--------|-------------|
| Number of iterations completed | 1000|
| Clashes at iteration 1 | 12|
| Final best clashes |0 |
| Did SA reach 0 clashes? (Yes / No) |Yes |

**Copy the printed timetable output here:**
```
[ Best Timetable:
Exam 1 → Slot 2
Exam 2 → Slot 4
Exam 3 → Slot 1
Exam 4 → Slot 3
Exam 5 → Slot 5
Exam 6 → Slot 2
Exam 7 → Slot 4
Exam 8 → Slot 1E ]
```

**Look at `plots/experiment_1.png` and describe what you see (2–3 sentences).**  
*Where does the biggest drop in clashes happen? Does the curve flatten out?*
```
[The graph shows a steep decrease in clashes during the initial iterations, indicating rapid improvement. After that, the curve gradually flattens as the algorithm converges. The biggest drop happens early, and later changes are minimal as it approaches an optimal solution. ]
```

---

## Experiment 2 — Effect of Cooling Rate

**Instructions:** In `sa_timetable.py`, find the `# EXPERIMENT 2` block in `__main__`.  
Copy it three times and run with `cooling_rate` = **0.80**, **0.95**, and **0.995**.  
Save plots as `experiment_2a.png`, `experiment_2b.png`, `experiment_2c.png`.

**Results table:**

| cooling_rate | Final clashes | Iterations completed | Reached 0 clashes? |
|-------------|---------------|----------------------|--------------------|
| 0.80        | 3              |  200                    |             NO       |
| 0.95        |  1             |     600                 |              NO      |
| 0.995       |  0             |        1000              |              YES      |

**Compare the three plots. What do you notice about how fast vs slow cooling affects the result? (3–4 sentences)**  
*Hint: Fast cooling = temperature drops quickly. Does it have time to explore well?*
```
[Fast cooling (0.80) reduces temperature quickly, so the algorithm stops exploring early and gets stuck in a suboptimal solution. Medium cooling (0.95) performs better but still does not fully explore the solution space. Slow cooling (0.995) allows more exploration and gradually improves the solution, leading to the best result. The slower the cooling, the smoother and more optimal the convergence. ]
```

**Which cooling_rate gave the best result? Why do you think that is?**
```
[ The best result is obtained with cooling_rate = 0.995. This is because the slow cooling allows the algorithm more time to explore different solutions and escape local optima. It gradually refines the solution to reach the optimal timetable with zero clashes.]
```

---

## Summary

**Complete this table with your best result from each experiment:**

| Experiment | Key setting | Final clashes | Main finding in one sentence |
|------------|-------------|---------------|------------------------------|
| 1 — Baseline | cooling_rate = 0.995 |0 | SA successfully finds optimal solution|
| 2 — Cooling rate | cooling_rate = ___ | 0|Slow cooling gives best results |

**In your own words — what is the most important thing you learned about Simulated Annealing from these experiments? (3–5 sentences)**
```
[ The most important thing I learned about Simulated Annealing is that it balances exploration and exploitation using temperature. At high temperatures, the algorithm explores widely and accepts worse solutions. As the temperature decreases, it becomes more selective and focuses on improving the solution. The cooling rate plays a critical role in performance. If cooling is too fast, the algorithm may get stuck, while slow cooling leads to better and more optimal results. ]
```

---

## Submission Checklist

- [ ] Student name and ID filled in
- [ ] Q1, Q2, Q3 answered
- [ ] Experiment 1: table filled, timetable pasted, plot observation written
- [ ] Experiment 2: results table filled (3 rows), observation and answer written
- [ ] Summary table completed and reflection written
- [ ] `plots/` contains: `experiment_1.png`, `experiment_2a.png`, `experiment_2b.png`, `experiment_2c.png`
