# PARALLEL MUSIC RECOMMENDER
## NUR SYAHMI BALQIS
## 2024211386

# Problem Statement
  Many or thousands of customers must get song recommendations simultaneously from a music streaming service. 
  It is too slow to process each user's listening history sequentially. 
  This assignment shows how music recommendations can be made faster by using concurrent and parallel programming.

# Objective
  * Create a system that analyzes user listening data to recommend music.
  * Use the sequential, concurrent (threading), and parallel (multiprocessing) versions.
  * Examine each sequential, concurrent, and parallel system's performance.
  * Explain why CPU-intensive jobs benefit from parallel programming.

# Three Implementations
* Sequential - One by one
* Concurrent - Threading
* Parallel - Multiprocessing

# Difference between Sequential, Concurrent & Parallel

## Sequential
* The tasks are carried out sequentially. Before starting the next task, the previous one must be finished.

## Concurrent
* By alternating between several duties, they advance. They alternate, but only one duty is completed at a time.
* Best for: I/O operations (file reads, network requests)

## Parallel
* Different CPU cores are used to conduct many tasks concurrently.
* Best for: CPU-intensive calculations (like similarity scoring)

# Code Structure
```ssh
# Sequential - one at a time
def run_sequential(data, users):
    for user in users:
        recommend(user)  # wait for finish

# Concurrent - threading
def run_concurrent(data, users):
    with ThreadPoolExecutor() as executor:
        executor.map(recommend, users)  # interleaved

# Parallel - multiprocessing  
def run_parallel(data, users):
    with ProcessPoolExecutor() as executor:
        executor.map(recommend, users)  # simultaneous
```

## Key Function

* generate_data() - Creates 10,000 listening record
* get_user_history() - Finds all songs a user listened to
* calculate_similarity() - Compares two user's music taste
* recommend_for_user() - Generates top 5 song recommendations

# Result & Performance Analysis
## Expected Output


## Summary 
* For CPU-intensive activities, parallel processing (multiprocessing) works best, achieving a speedup of about three times.
* Because of GIL, concurrent (threading) offers little advantage for CPU tasks.
* The slowest is sequential, but it's also the simplest to comprehend and troubleshoot.
