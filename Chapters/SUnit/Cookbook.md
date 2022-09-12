## The SUnit cookbook
	instanceVariableNames: 'configurationSelector formatterClass contextClass'
	classVariableNames: ''
	package: 'Enlumineur-Tests'
	^ ParametrizedTestMatrix new
		addCase: { (#formatterClass -> BIEnlumineurPrettyPrinter) . (#contextClass -> BIEnlumineurContext) };
		yourself

	^ ParametrizedTestMatrix new
		addCase: { #number1 -> 2. #number2 -> 1.0. #result -> 3 };
		addCase: { #number1 -> (2/3). #number2 -> (1/3). #result -> 1 };
		yourself

	^ ParametrizedTestMatrix new
		forSelector: #item1 addOptions: { 1. 'a'. $c };
		forSelector: #item2 addOptions: { 2. 'b'. $d };
		forSelector: #collectionClass addOptions: { Set. Bag. OrderedCollection }

	^ ParametrizedTestMatrix new
		forSelector: #option1 addOptions: #(a b c);
		forSelector: #option2 addOptions: {[1].[2].[3]};
		yourself.

	^ ParametrizedTestMatrix new
			addCase: { #importer -> CBkCollectorDLittleImporter new };
		yourself.

	^ ParametrizedTestMatrix new
			addCase: { #importerClass -> CBkCollectorDLittleImporter };
		yourself.

CbkDlittleImporterTest >> setUp 
	super setUp.
	importer := importerClass new.
	
CbkDlittleImporterTest >> importerClass: anImporterClass
	importerClass := anImporterClass
deny:description:` take a second argument which is a message string that
		self should: [ empty at: 5 ] raise: Error.
		self should: [ empty at: 5 put: #zork ] raise: Error
	self assert: aDateAndTime asDate = ('February 29, 2004' asDate translateTo: 2 hours).

testAsDate
	self
		assert: aDateAndTime asDate
		equals: ('February 29, 2004' asDate translateTo: 2 hours).
e := 42.
self assert: e = 23 description: 'expected 23, got ', e printString
...
deny:description:
should:description:
shouldnt:description:
>>> 1 run, 1 passed, 0 failed, 0 errors
>>> 5 run, 5 passed, 0 failed, 0 errors
	^ true

	| newCompiledMethod originalCompiledMethod |
	(self class environment hasClassNamed: #Compiler) ifFalse: [ ^ self skip ].
	...
	self
		assert: each even
		description: each printString, ' is not even'
		resumable: true ]
	instanceVariableNames: ''
	...


MyTestResource >> setUp
	...

MyTestCase class >> resources
	"Associate the resource with this class of test cases"

	^ { MyTestResource }
MyTestCase >> setUp has run.
MyTestCase >> testOne has run.
MyTestCase >> tearDown has run.
MyTestCase >> setUp has run.
MyTestCase >> testTwo has run.
MyTestCase >> tearDown has run.
MyTestResource >> tearDown has run.
	Transcript show: 'MyTestCase>>setUp has run.'; cr

MyTestCase >> tearDown
	Transcript show: 'MyTestCase>>tearDown has run.'; cr

MyTestCase >> testOne
	Transcript show: 'MyTestCase>>testOne has run.'; cr

MyTestCase >> testTwo
	Transcript show: 'MyTestCase>>testTwo has run.'; cr

MyTestCase class >> resources
	^ Array with: MyTestResource

MyTestResource >> setUp
	Transcript show: 'MyTestResource>>setUp has run'; cr

MyTestResource >> tearDown
	Transcript show: 'MyTestResource>>tearDown has run.'; cr
	^ self classWithExamplesToTest class methods 
		select: [ :each | (each selector beginsWith: 'example') and: [ each numArgs = 0 ] ]
		thenCollect: [ :each | each selector ]
 	example := self class classWithExamplesToTest perform: testSelector asSymbol

	^ true
	"I should inherit from an Abstract superclass but not from a concrete one by default, 
	unless I have no testSelectors in which case I must be expecting to inherit them from my superclass.  
	If a test case with selectors wants to inherit selectors from a concrete superclass, override this to true in that subclass."
	
	^self ~~ self lookupHierarchyRoot
		and: [self superclass isAbstract or: [self testSelectors isEmpty]]