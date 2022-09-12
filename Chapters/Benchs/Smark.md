## Performance testing with SMark
    baseline: 'SMark';
    repository: 'github://smarr/SMark';
    load.
  ^n <= 1 
  	ifTrue: [ n ] 
	ifFalse: [ (self fib: (n - 1)) + (self fib: (n - 2)) ]
2 execution: 1046 milliseconds
3 execution: 1098 milliseconds
4 execution: 1069 milliseconds
5 execution: 1085 milliseconds
	instanceVariableNames: ''
	classVariableNames: ''
	package: 'SMark-Demo'
	self fib: 40.
Benchmark Fib40
Fib40 total: iterations=1 runtime: 1099ms
Benchmark Fib40
Fib40 total: iterations=25 runtime: 1022.7ms +/-1.5
  ^self onCog: [ SMarkCogRunner ] else: [ SMarkRunner ]
result := SMarkLoops run.
stream := TextStream on: String new.
SMarkSimpleStatisticsReporter reportFor: result on: stream.
testReport := stream contents.