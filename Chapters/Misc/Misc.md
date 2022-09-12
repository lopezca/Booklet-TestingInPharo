## Miscellaneous
	"Convert to a ByteArray with the ascii values of the string."
	"'a' asByteArray >>> #[97]"
	"'A' asByteArray >>> #[65]"
	"'ABA' asByteArray >>> #[65 66 65]"

	| b |
	b := ByteArray new: self byteSize.
	1 to: self size * 4 do: [:i |
		b at: i put: (self byteAt: i)].
	^ b
	"return myself or a copy shortened by ellipsis to smallSize"
	"('abcd' contractTo: 10) >>> 'abcd'"
	"('Pharo is really super cool' contractTo: 10) >>> 'Phar...ool'"
	"('A clear but rather long-winded summary' contractTo: 18) >>> 'A clear ...summary'"
	
	| leftSize |
	self size <= smallSize
		ifTrue: [^ self].  "short enough"
	smallSize < 5
		ifTrue: [^ self copyFrom: 1 to: smallSize].    "First N characters"
	leftSize := smallSize-2//2.
	^ self copyReplaceFrom: leftSize+1		"First N/2 ... last N/2"
		to: self size - (smallSize - leftSize - 3)
		with: '...'
	package: 'SUnit-Extensions'

	^ self methods
		select: [ :each | (each hasPragmaNamed: #example) and: [ each selector isUnary ] ]
		thenCollect: [ :each | each selector ]
	<gtExample>
	| element mouseLeave mouseMove mouseEnter |

	element := self blueElement.
	element size: 100@100.
	element relocate: 100@100.

	mouseLeave := mouseMove := mouseEnter := 0.

	element addEventHandlerOn: BlMouseMoveEvent do: [ mouseMove := mouseMove + 1 ].
	element addEventHandlerOn: BlMouseEnterEvent do: [ mouseEnter := mouseEnter + 1 ].
	element addEventHandlerOn: BlMouseLeaveEvent do: [ mouseLeave := mouseLeave + 1 ].
	
	BlSpace simulateMouseMoveOutside: element.

	self assert: mouseMove equals: 0.
	self assert: mouseEnter equals: 0.
	self assert: mouseLeave equals: 0.

	^ element