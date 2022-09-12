## Object validation with StateSpecs
  baseline: 'StateSpecs';
  repository: 'github://dionisiydk/StateSpecs';
  load.
spec validate: 10. 
>>> a SpecOfValidationSuccess

spec validate: 'some string'. 
>>> a SpecOfValidationFailure(Got 'some string' but it should be an instance of SmallInteger)
>>> true
>>> false
spec not validate: 'some string'. "==> a SpecOfValidationSuccess"
y should equal: 10
>>> a SpecOfObjectSuperclass(should be a kind of Number)
Instance of: String. 
>>> a SpecOfObjectClass(should be an instance of String)
Equal to: 'test'. 
>>> a SpecOfEquality(should equal 'test')
>>> a SpecOfEquality(should equal 'test')

Equal to: 10.0123 within: 0.01. 
>>>  a SpecOfApproxEquality(should be within 0.01 of 10.0123)
>>> fail with message: Got '3' but it should not equal '3'
1 should not be: 1.
3 should not equal: 3.
>>> false
expected := #(1 2 3).

actual should beInstanceOf: expected class.
actual should equal: expected.
>>> true 
#(1 2 3) asSet should equal: #(2 1 3). 
>>> true 
>>> Fails #(1 2 3)" but it should equal in order to "#(2 1 3)
>>> Fails
>>> false"
>>> true 
>>> true 
10.123 should equal: 10.1 within: 0.01 "
>>> Fails 
>>> Fails
>>> Fails
>>> Fails
>>> Fails
>>> Fails
>>> Fails
>> Fails
>>> Fails
>>> Fails
>>> Fails
>>> Fails
>>> Fails
'test string' should beginWith: 'Test' caseSensitive: true
'string for test' should endWith: 'Test' caseSensitive: true
'test string' should matchRegex: '^Test' caseSensitive: true
>>> Fails
>>> true
errorInstance := Error new messageText: 'test error'.
[ error signal ] should raise: errorInstance
>>> Fails
spec := SpecOfBooleanProperty fromMessage: (Message selector: #isEmpty)
spec validate: #()
>>> true
spec validate: 5
>>> Fail