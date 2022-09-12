## UI testing

	| model |
	model := String.
	spApplication := ClassVisualizerPresenter on: model.
	self assert: spApplication model equals: model.
	self
		assert: spApplication textPresenter text
		equals: model classDefinitions first definitionString.
	self
		assert: spApplication morphPresenter morph contents
		equals: model name

	"As we have initialized the tree with Object as its roots. The class OrderedCollection is a subclass of Object. We would simulate that a user selectes OrderedCollection from the tree presenter."

	spApplication := ClassVisualizerPresenter on: Object.
	spApplication hierarchyTreePresenter selectItem: OrderedCollection.
	self
		assert: spApplication hierarchyTreePresenter selectedItem
		equals: OrderedCollection.
	self
		assert: spApplication textPresenter text
		equals: OrderedCollection classDefinitions first definitionString.
	self
		assert: spApplication morphPresenter morph contents
		equals: OrderedCollection name

	| previousColor |
	spApplication := ClassVisualizerPresenter on: Object.
	previousColor := spApplication morphPresenter morph color.
	spApplication colorButton click.
	self
		deny: spApplication morphPresenter morph color
		equals: previousColor

	spApplication := ClassVisualizerPresenter on: Object.
	self deny: spApplication textPresenter isEditable

	| window |
	spApplication := ClassVisualizerPresenter on: Object.
	window := spApplication openWithSpec.
	self assert: window isBuilt.
	self assert: window title equals: ClassVisualizerPresenter title.
	self assert: window initialExtent equals: 600 @ 400.
	window close