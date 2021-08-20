# Intro
To implement a distributed MapReduce, consisting of two programs, the coordinator and the worker. There will be just one coordinator process, and one or more worker processes executing in parallel. The workers will talk to the coordinator via RPC. Each worker process will ask the coordinator for a task, read the task's input from one or more files, execute the task, and write the task's output to one or more files. The coordinator should notice if a worker hasn't completed its task in a reasonable amount of time (for this lab, use ten seconds), and give the same task to a different worker.

the implementation should be in mr/coordinator.go, mr/worker.go, and mr/rpc.go.

# Run
```py
# build
go build -race -buildmode=plugin ../mrapps/wc.go

# run the coordinator(in the main directory)
rm mr-out*
go run -race mrcoordinator.go pg-*.txt

# run some workers
go run -race mrworker.go wc.so
```

# Result
When the workers and coordinator have finished, look at the output in mr-out-*. When you've completed the lab, the sorted union of the output files should match the sequential output
