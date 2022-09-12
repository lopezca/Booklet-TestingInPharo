## MockObject and Teachable: Two super simple mocking approaches
	slots: { #mock };
	package: 'SUnit-MockObjects-Tests'

	super setUp.
	mock := MockObject new.
	mock
		on: #meaningOfLife 
		respond: 42. 
	mock 
		on: #secondMeaning
		respond: 84.	

	self assert: mock meaningOfLife equals: 42.
	self assert: mock secondMeaning equals: 84.
	self verify: mock

	super setUp.
	mock := MockObject new.
	mock
		on: #meaningOfLife: 
		with: 22
		respond: 42. 
	mock 
		on: #secondMeaning:and:
		with: 32
		with: 64
		respond: 84.

	self should: [ self assert: (mock meaningOfLife: 33) equals: 42] raise: TestFailure

	self assert: (mock meaningOfLife: 22) equals: 42.
	self assert: (mock secondMeaning: 32 and: 64) equals: 84
	on: #messageToBeMocked:withArguments:
	with: 1
	with: 'two'
	on: #messageToBeMocked:withArguments:
	with: MockObject any
	with: 'two'
	repository: 'github://astares/Pharo-Teachable/src';
	baseline: 'Teachable';
	load 
teachable := Teachable new.
teachable
    whenSend: #help return: 'ok';
     whenSend: #doit evaluate: [ 1 inspect ];
     acceptSend: #noDebugger;
     whenSend: #negate: evaluate: [ :num | num negated ].
	"this will return the string 'ok'"
teachable doit. 
	"this will open the inspector on the SmallInteger 1"
teachable noDebugger. 
	"this will accept the send of #noDebugger and return the teachable"
teachable negate: 120 
	"this will return -120"