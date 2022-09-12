## Mocketry
  baseline: 'Mocketry';
  repository: 'github://dionisiydk/Mocketry';
  load.
result should equal: 'XII'.
subscriber should receive eventReceived: testEvent.
warehouse := Mock new.
(warehouse stub has: 50 of: #product) willReturn: true.

order fillFrom: warehouse.

warehouse should receive remove: 50 of: #product.
	| creditCard cart |
	creditCard := Mock new.
	cart := ShoppingCart payment: creditCard.

	cart checkout.

	creditCard should not receive charge: Any.
	"empty implementation"
	super setUp.
	priceCatalog := Mock new.
	creditCard := Mock new.
	cart := ShoppingCart catalog: priceCatalog payment: creditCard.
	(priceCatalog stub priceOf: #sku1) willReturn: 80.

	cart addSKU: #sku1.
	cart checkout.

  (creditCard should receive charge: 80) once.
	sku := aString.
	creditCard charge: (priceCatalog priceOf: sku).
	sku ifNotNil:
		[creditCard charge: (priceCatalog priceOf: sku)]
	(priceCatalog stub priceOf: #sku1) willReturn: 10.
  (priceCatalog stub priceOf: #sku2) willReturn: 30.
  (priceCatalog stub priceOf: #sku3) willReturn: 50.
	cart addSKU: #sku1.
	cart addSKU: #sku2.
	cart addSKU: #sku3.

	cart checkout.

  creditCard should receive charge: 90.
	super initialize.
	skus := OrderedCollection new.
	skus add: aString.
	skus ifNotEmpty:
		[ creditCard charge: (skus sum: [ :each | priceCatalog priceOf: each ])]
	self prices: {#sku1 -> 10. #sku2 -> 30. #sku3 -> 50}.
	cart addSKU: #sku1.
	cart addSKU: #sku2.
	cart addSKU: #sku3.

	cart checkout.

	creditCard should receive charge: 90.
	associations do: [:each |
			(priceCatalog stub priceOf: each key) willReturn each value].
	skus ifNotEmpty:
		[creditCard charge: self orderPrice]
	^ skus sum: [:each | priceCatalog priceOf: each]
	self prices: {#sku1 -> 30. #sku2 -> 70.}.
	cart addSKU: #sku1.
	cart addSKU: #sku2.
	cart removeSKU: #sku2.

  cart checkout.

  creditCard should receive charge: 30.
	skus remove: aSymbol.
	super setUp.
	priceCatalog := Mock new.
	discountCalculator := Mock new.
	creditCard := Mock new.
	cart := ShoppingCart catalog: priceCatalog discount: discountCalculator payment: creditCard.
	self prices: {#sku1 -> 20. #sku2 -> 30}.
	(discountCalculator stub calculateDiscount: 50) willReturn: 10.
	cart addSKU: #sku1.
	cart addSKU: #sku2.

	cart checkout.

  creditCard should receive charge: 40.
	| orderPrice discountPrice |
	skus ifNotEmpty:
		[orderPrice := self orderPrice.
		discountPrice := self discountPrice: orderPrice.
		creditCard charge: orderPrice - discountPrice]
	^ discountCalculator calculateDiscount: orderPrice
	|purchase|
	self prices: {#sku1 -> 10. #sku2 -> 30}.
	cart addSKU: #sku1.
	cart checkout.
	cart addSKU: #sku2.
	cart checkout.

  [creditCard receive charge: 10.
  creditCard receive charge: 30] should beDoneInOrder
a Mock(creditCard) charge: 40 returned default mock(34614).
	| orderPrice discountPrice |
	skus ifNotEmpty:
		[orderPrice := self orderPrice.
		discountPrice := self discountPrice: orderPrice.
		skus removeAll.
		creditCard charge: orderPrice - discountPrice]
	self prices: {#sku -> 25}.
	cart addSKU: #sku.

	(creditCard stub charge: 25) willRaise: PaymentError new.
	[cart checkout] should raise: PaymentError.

	(creditCard stub charge: Any) willReturn: true.
	cart checkout.
	(creditCard should receive charge: 25) twice.
	| orderPrice discountPrice |
	skus ifNotEmpty:
		[orderPrice := self orderPrice.
		discountPrice := self discountPrice: orderPrice.
		creditCard charge: orderPrice - discountPrice.
		skus removeAll]
	| catalog |
	catalog := PriceCatalogDictionary withPrices {#sku1 -> 10}.
	(catalog priceOf: #sku1) should equal: 10.
	| response |
	response := ZnClient new
		url: 'http://example.com/rest/sku/', sku;
		get;
		response.
	^ self parseResponse: repsonse.
mock stub someMessage willReturn: 100.
mock someMessage should be: 100.
rect stub width willReturn: 1000.

rect area should be: 3000 "area = width * height"

DateAndTime now should be: #constantValue.

mock stub anyMessage willreturn:: 100.

mock someMessage should be: 100.
mock someMessage2 should be: 100.

mock := Mock new.
mock someMessage should be: 100.

rect := 0@0 corner: 2@3.
rect stub.

rect area should be: 100.
rect width should be: 100.

rect := 0@0 corner: 2@3.
rect stub.

rect area should be: 300.

rect2 := 0@0 corner: 4@5.
rect2 stub.

rect2 area should be: 500
mock stub messageWith: Any and: arg2
mock stub messageWith: [:arg | true]
mock stub messageWith: (Kind of: String) and: arg2
mock stub messageWith: (Instance of: Float) & (Satisfying for: [:arg | arg > 10]).
(mock stub messageWith: (Instance of: SmallInteger)) willReturn: #anyInt.
(mock stub messageWith: (Kind of: String)) willReturn: #anyString.
(mock stub messageWith: 10) willReturn: #ten.

(mock messageWith: 10) should be: #ten.
(mock messageWith: 20) should be: #anyInt.
(mock messageWith: 'test' should be: #anyString
mock someMessage should be: #result.
[mock someMessage] should raise: ZeroDivide.
(mock someMessageWith: #arg) should be: #result.
(mock someMessageWith: #arg1 and: #arg2) should equal: 'arg1arg2'.
mock someMessage should be: #result1.
mock someMessage should be: #result2
mock someMessage should be: mock.
mock stub someMessage
	when: [ flag ] is: (Kind of: Boolean);
	when: [ flag ] is: true;
	when: [ flag ] satisfy: [ :object | true or: [ false ] ].

flag := true.
mock someMessage. "does not fail"

flag := false.
mock someMessage "will fail immediately on call by last condition: flag should be true"

flag := #flag.
mock someMessage "will fail immediately on call by first condition: flag should be boolean"
[ mock someMessage ] fork. "will fail immediately on call".

mock stub someMessage shouldBeSentInAnotherProcess.
[ mock someMessage ] fork. "will not fail".
mock someMessage. "will fail immediately on call"

mock stub someMesage willReturn: #default.
mock stub someMessage willReturn: 300; use: 3.
mock stub someMessage willReturn: 200; useTwice.
mock stub someMesage willReturn: 100 useOnce.

mock someMessage should be: 200.
mock someMessage should be: 200.

mock someMessage should be: 300.
mock someMessage should be: 300.
mock someMessage should be: 300.

mock someMessage should be: #default

automock := mock someMessage.

automock should beInstanceOf: MockForMessageReturn.
returnedMock := mock someMessage.

result := returnedMock ifFalse: [ #falseBranch ] ifTrue: [ #trueBranch ].

result should be: #falseBranch.
returnedMock should be: false
returnedMock := mock someMessage.

result := 1 + returnedMock.
result should equal: 1.
returnedMock should equal: 0
rect := 0@0 corner: 2@3.
rect stub.

[ mock someMessage willReturn: 10.
rect width willReturn: 1000 ] should expect.

mock someMessage should be: 10.
rect area should be: 3000.

mock someMessage.

mock should receive someMessage.
mock should not receive anotherMessage

rect stub "it should be here to enable message interception"
rect area

rect should receive width. "area = width * height"
DateAndTime midnight.

DateAndTime should receive now. "inside midnight #now is called"
rect := 0@0 corner: 2@3.
rect stub.

mock width.
rect area.

Any should receive width. "it will check that mock and rect received message #width"
Any should receive area "it will fail because mock not received #area message".

mock someMessage should be: 100.

mock should receive anyMessage.
rect := 0@0 corner: 2@3.
rect stub.

mock someMessage.

Any should receive anyMessage. "will fail because rect not received any message".

rect width.

Any should receive anyMessage. "will not fail because both objects received at least one message"
rect stub.

rect area.

rect2 := 0@0 corner: 4@5.
rect2 width.

(Kind of: Rectangle) should receive width. "will not fail because both rect's received message #width"
(Kind of: Rectangle) should receive area "will fail because rect2 not received message #area"

mock := Mock new.
(Kind of: Rectangle) should receive width. "will not fail because mock is not kind of Rectangle"

(mock messageWith: 10) should be: #ten.
(mock messageWith: 'test' should be: #anyString.

mock should receive messageWith: 10.
mock should receive messageWith: (Instance of: SmallInteger).
mock should receive messageWith: 'test'.
mock should receive messageWith: (Kind of: String).
mock should receive messageWith: [:arg | arg isNumber].
mock someMessageWith: Arg argName.

mock someMessageWith: #argValue.

Arg argName should be: #argValue.
Arg argName fromLastCall should be: #value3.
(Arg argName fromCall: 2) should be: #value2.

rect := 0@0 corner: 2@3.
mock someMessageWith: rect.
rect area.

Arg rectangle should be: rect.
Arg rectangle should receive width.

mock someMessage.
mock should receive someMessage once.

mock someMessage.
mock should receive someMessage twice.

mock someMessage.
mock should receive someMessage exactly: 3.
mock should receive someMessage atLeast: 2.
mock should receive someMessage atMost: 3.
mock should receive someMessage atLeast: 1 atMost: 5.
mock2 := Mock new.

mock someMessage; someMessage.
mock2 someMessage.

Any should receive someMessage twice. "will fail because mock2 received #someMessage only once"

mock2 someMessage.
Any should receive someMessage twice. "will not fail because both mocks received #someMessage twice"
rect stub.

rect area.

rect should receive area which should equal: 6.
rect should receive width which should beKindOf: Number
result := mock someMessage.
result should beReturnedFrom: [ mock someMessage ].
rect := 0@0 corner: 2@3.
rect stub.

mock someMessage.
rect area.

[ rect width.
mock someMessage ] should beDone.

[ mock someMessage.
rect width ] should beDoneInOrder.
mock2 := Mock new.

[ mock1 someMessage. mock2 someMessage2 ]
   should lenient satisfy:
[ mock2 someMessage2.
mock1 someMessage willReturn: 'some' ].
mock2 := Mock new.

[ mock1 someMessage. mock2 someMessage2 ]
   should strictly satisfy:
[ mock1 someMessage willReturn: 'some'.
mock2 someMessage2 ].