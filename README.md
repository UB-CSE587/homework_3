# HomeWork 3

This assignment provides hands-on experience with writing and executing Spark in Python. You’ll start by installing PySpark, then implement functions to calculate edit distance between text strings and create efficient inference code for an MLP model. At last, you’ll modify a bird flock simulation code to utilize Spark for enhanced performance.

General Homework Requirements:

- Work Environment: This homework can be written in Pyspark/Python.
- Programming: Your submission must be a executable python script.
- Academic Integrity: You will get an automatic F for the course if you violate the academic integrity policy.
- Teams: This homework is an individual assignment. You are not permitted to work with anyone else on this assignment. All work submitted must be yours and yours alone.


---

## 1. Task
### 1.1 Edit Distance
A script for loading text data and computing the edit distance is provided in [`edit_dist.py`](https://github.com/UB-CSE587/homework_2/blob/main/edit_dist.py), which includes a basic implementation using a `for` loop. Revise this code to include:
- A Spark version
- A multi-process version

Record the execution time for each version when computing pairwise edit distances for 1,000 sentences.

### 1.2 MLP Inference
Inference code for an MLP classifier is available in [`MLP.py`](https://github.com/UB-CSE587/homework_2/blob/main/MLP.py). Update this code to include a Spark-based implementation for more efficient inference.

### 1.3 Flock Move Simulation using Spark
In this task, you will work with a [bird flock](https://en.wikipedia.org/wiki/Flock_(birds)) simulation, where each bird’s position is represented by a point in 3D space. Each bird follows movement rules based on flock dynamics:

1. **Alignment**: Birds attempt to stay close to the leader bird, which follows a determined path with uniform velocity.
2. **Separation**: Birds maintain distance from nearby neighbors. If a bird gets too close to a neighbor (within a threshold), it moves away.
3. **Cohesion**: Birds strive to stay with the flock. If a bird is too far from its nearest neighbor (beyond a threshold), it moves closer.
4. **Velocity Constraints**: Flying speed is restricted to a certain range—too slow and the bird risks falling; too fast, and it exceeds physical limits.

A demonstration of the bird flock movement is shown below:
![bird](bird_simulation.gif)

Please update the provided simulation code ([`bird.py`](https://github.com/UB-CSE587/homework_2/blob/main/bird.py)) to utilize Spark for parallel processing of position updates for all birds. All necessary hyperparameters (thresholds, max/min values) are included in the script, along with a basic implementation using a for-loop to update bird positions. Revise this to add a Spark-based implementation to handle position updates more efficiently. You need to write and submit a separate python file: `bird_spark.py`.

---

## 2. Code Evaluation
The evaluation will be conducted on the same machine to ensure consistency across all implementations.

- **Task 1.1**, 
Submitted code will be tested by a command like:
```
python edit_dist.py --csv_dir /path/to/csv --num_sentences n
```
And at the end of your code, it should print the time cost for each version (for-loop, multi-process, and Spark) in this format:
```
print(f"Time cost (Spark, multi-process, for-loop): [{time_1:.3f}, {time_2:.3f}, {time_3:.3f}]")
```

- **Task 1.2**, Submitted code will be tested by a command like:
```
python MLP.py --n_input n --hidden_dim d --hidden_layer l
```
And at the end of your code, it should print the time cost in this format:
```
print(f"Time cost for spark and non-spark version: [{time_1:.3f},  {time_2:.3f}] seconds")
```

- **Task 1.3**, You need to submit a python script `bird_spark.py` for your spark implementation, which will be tested directly by: `python bird_spark.py`. And your code is expected to generate a gif image similar to the demo showed above. (The plot function is also provided in the `get_gif.py`.) In addition, your code should print time cost per frame at the end of your code in this format:
```
print(f'Average time cost per frame: {mean_time:.4f}')
```

## 3. Report:

- **Task 1.1**, In your report, you are required to report time cost of three implementation with different numbers of sentences: `[10, 50, 100, 250, 500, 1000]`.
- **Task 1.2**, test and report the time costs with values for `n_input` set to `[1000, 5000, 10000, 50000, 100000]`, keeping `hidden_dim` and `hidden_layer` as default. 
- **Task 1.3**, you are required to run the simulation using both the Spark and non-Spark implementations with `[200, 1,000, 5,000, 10,000]` birds for `500` frames. Record the time cost per frame for both implementations and include these results in your report, along with a discussion of your observations.

- Present numerical results in your report, either as tables or plots for clarity, and write discussion on any trends observed.
- Reports with obvious signs of AI-generated content will result in a -5 point deduction for the course. Ensure that the report reflects original work without clear indicators of AI generation. Using AI tools for grammar correction is allowed.


---

## 4. Submission Format:
You are expected to submit a zip file, called `<UBIT_Name>.zip`, in UBLearn consists all your code, a gif image for task 1.3, and your report in pdf in your zip file. The zip file should be organized as following:
```
<UBIT_Name>
--<UBIT_Name>.pdf
--edit_dist.py
--MLP.py
--bird_spark.py
```

---

## 5. Scoring

The score will be assigned as follows:

- **Task 1.1**: Successful code execution – 10 points (must print reasonable time cost in required format).
- **Task 1.2**: Successful code execution – 10 points (must print reasonable time cost in required format).
- **Task 2**: Successful code execution – 20 points (must print reasonable time cost in required format and generate a meaningful GIF image).
- **Report Quality**: 60 points (must include all numerical results, with clear descriptions and discussion).

