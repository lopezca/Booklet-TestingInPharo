## SUnit by example
	instanceVariableNames: ''
	classVariableNames: ''
	package: 'MySetTest'
	| full empty |
	full := Set with: 5 with: 6.
	empty := Set new.
	self assert: (full includes: 5).
	self assert: (full includes: 6).
	self assert: (empty includes: 5) not
	| full empty |
	full := Set with: 5 with: 6.
	empty := Set new.
	self assert: (empty occurrencesOf: 0) equals: 0.
	self assert: (full occurrencesOf: 5) equals: 1.
	full add: 5.
	self assert: (full occurrencesOf: 5) equals: 1
	instanceVariableNames: 'full empty'
	classVariableNames: ''
	package: 'MySetTest'
	super setUp.
	empty := Set new.
	full := Set with: 5 with: 6
	
	self assert: (full includes: 5).
	self assert: (full includes: 6).
	self assert: (empty includes: 5) not
	
	self assert: (empty occurrencesOf: 0) equals: 0.
	self assert: (full occurrencesOf: 5) equals: 1.
	full add: 5.
	self assert: (full occurrencesOf: 5) equals: 1
	full remove: 5.
	self assert: (full includes: 6).
	self deny: (full includes: 5)
	full remove: 5.
	self assert: (full includes: 7).
	self deny: (full includes: 5)

MyExampleSetTest debug: #testRemove