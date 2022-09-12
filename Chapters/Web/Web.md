## Testing web applications with Parasol
    baseline: 'Parasol';
    repository: 'github://SeasideSt/Parasol/repository';
    load: 'tests'.
	instanceVariableNames: ''
	classVariableNames: ''
	package: 'FT-Parasol'

	| driver |
	driver := BPRemoteWebDriver withCapabilities: BPChromeOptions new.
	driver get: 'https://pharo.org/'.
	self assert: 'Pharo - Welcome to Pharo!' equals: driver getTitle.
	driver close.
	instanceVariableNames: ''
	classVariableNames: ''
	package: 'FT-Parasol'
driver := BPRemoteWebDriver withCapabilities: BPChromeOptions new.
	instanceVariableNames: 'driver'
	classVariableNames: ''
	package: 'FT-Parasol'
	super setUp.
	driver := BPRemoteWebDriver withCapabilities: BPChromeOptions new.
	driver get: 'https://pharo.org/'
	super tearDown.
	driver quit
	self assert: 'Pharo - Welcome to Pharo!' equals: driver getTitle.
    <input id="fullName" name="textInfo" type="text"/>
    <input id="submitButton" type="submit"/>
</form>
linkPharo := driver findElementByPartialLinkText: 'Go to'.
  <input id="inputField" name="textInfo" type="text"/>
  <input id="submitButton" type="submit"/>
</form>
<a class="testclass2">foobar</a>
testClassTwo := driver findElementByClassName: 'testclass2'.
 	<p id="testDiv1p" class="c1"></p>
    </div>
    <div id="testDiv2">
 	<p id="testDiv2p1" class="c2"></p>
 	<p id="testDiv2p2" class="c1"></p>
 	<p id="testDiv2p3" class="c1"></p>
    </div>
	<input type="checkbox" name = "same" value="on">Same checkbox in Div1</input>
</div>
<div id = "div2">
	<input type="checkbox" name = "same" value="on">Same checkbox in Div2</input>
</div>
<body>
<h1>Sign in</h1>
<form id="loginForm">
    <input name="username" type="text" />
    <input name="password" type="password" />
    <button name="login" type="submit" class= "btn btn-primary">Login</button>
    <a href="forgotPassworsd.html">Do you forgot your password?</a>
    <p class="content">
        "Are you new here?"
        <a href="register.html">Create an account</a>
    </p>
</form>
</body>
<html>
password := driver findElementByName: 'password'
password sendKeys: 'xxxxxxx'.
loginButton click.
	instanceVariableNames: 'driver'
	classVariableNames: ''
	package: 'Example-Parasol-Tests'
	super setUp.
	driver := BPRemoteWebDriver withCapabilities: BPChromeOptions new.
	driver get: self baseURL

EPTest >> baseURL
	^ 'http://newtours.demoaut.com/'
	driver quit.
	super tearDown
	| title |
	title := driver getTitle.
	self assert: title equals: 'Welcome: Mercury Tours'
    <td width="80%">
    <font face="Arial, Helvetica, sans-serif, Verdana" size="2">
        Atlanta to Las Vegas
    </font>
    </td>
    <td width="20%">
    <div align="right">
    <font face="Arial, Helvetica, sans-serif, Verdana" size="2">
        <b>$398</b>
    </font>
    </div>
    </td>
</tr>
	instanceVariableNames: ''
	classVariableNames: ''
	package: 'Example-Parasol-Tests'

self assert: ((driver findElementByXPath: '/html/body/div/table/tbody/tr/td[2]/table/tbody/tr[4]/td/table/tbody/tr/td[2]/table/tbody/tr[2]/td[1]/table[1]/tbody/tr[3]/td/table/tbody/tr[1]/td[1]/font') getText)
     equals: 'Atlanta to Las Vegas'.
self assert: ((driver findElementByXPath: '/html/body/div/table/tbody/tr/td[2]/table/tbody/tr[4]/td/table/tbody/tr/td[2]/table/tbody/tr[2]/td[1]/table[1]/tbody/tr[3]/td/table/tbody/tr[1]/td[2]/div/font/b') getText)
    equals: '$398'
	^ driver findElementByXPath: '/html/body/div/table/tbody/tr/td[2]/
	table/tbody/tr[4]/td/table/tbody/tr/td[2]/table/tbody/tr[2]/td[1]/
	table[1]/tbody/tr[3]/td/table/tbody/tr[1]/td[1]/font'

EPHomePageTest >> priceFlightFromAtlantaToLasVegas
	^ driver findElementByXPath: '/html/body/div/table/tbody/tr/td[2]/
	table/tbody/tr[4]/td/table/tbody/tr/td[2]/table/tbody/tr[2]/
	td[1]/table[1]/tbody/tr[3]/td/table/tbody/tr[1]/td[2]/div/font/b'
	self 
		assert: self descriptionFlightFromAtlantaToLasVegas getText
		equals: 'Atlanta to Las Vegas'.
	self 
		assert: self priceFlightFromAtlantaToLasVegas getText
		equals: '$398'
	instanceVariableNames: ''
	classVariableNames: ''
	package: 'Example-Parasol-Tests'
	(driver findElementByLinkText: 'REGISTER') click
	super setUp.
	self clickInRegisterButton
	| title |
	title := driver getTitle.
	self assert: title equals: 'Register: Mercury Tours'
<td align=right>
<font face="Arial, Helvetica, sans-serif" size="2">
<b>First Name: </b>
</font>
</td>
<td>
<input maxlength=60 name="firstName" size="20">
</td>
</tr>
 <tr>
<td align=right>
<font face="Arial, Helvetica, sans-serif" size="2">
<b>Last Name: </b>
</font>
</td>
<td>
<input maxlength=60 name="lastName" size="20">
</td>
</tr>
<tr>
<td align=right>
<font face="Arial, Helvetica, sans-serif" size="2">
<b>Phone:</b>
</font>
</td>
<td>
<input maxlength="20" name="phone" size="15">
</td>
</tr>
<tr>
<td align=right>
<font face="Arial, Helvetica, sans-serif" size="2">
<b>Email:</b>
</font>
</td>
<td>
<input name="userName" id="userName" size="35" maxlength="64">
</td>
</tr>
	^ driver findElementByName: 'firstName'
	self firstNameField sendKeys: 'Jhon'.
	self lastNameField sendKeys: 'Stuart'.
	self phoneField sendKeys: '10276123'.
	self emailField sendKeys: 'example@mail.com'
	self fillInformationToContactSection.
	self assert: (self firstNameField getAttribute: 'value') equals: 'Jhon'.
	self assert: (self lastNameField getAttribute: 'value') equals: 'Stuart'.
	self assert: (self phoneField getAttribute: 'value') equals: '10276123'.
	self assert: (self emailField getAttribute: 'value') equals: 'example@mail.com'
	(self countryField findElementsByTagName: 'option') do: [ :each |
		(each getAttribute: 'selected')
			ifNotNil: [ ^ each ] ]
	self assert: (self getSelectedOfCountry getText) equals: 'UNITED STATES '.
	(driver findElementByName: 'register') click
	^ driver findElementByXPath: '/html/body/div/table/tbody/tr/td[2]/
table/tbody/tr[4]/td/table/tbody/tr/td[2]/table/tbody/tr[3]/td/p[2]/font'
	<timeout: 10>
	self sendInformationToContactSection.
	self sendInformationToMailingSection.
	self sendInformationToUserSection.
	self clickInSubmitButton.
	self 
		assert: (self descriptionText getText)
		equals: 'Thank you for registering.
You may now sign-in using the user name
and password you''ve just entered.'