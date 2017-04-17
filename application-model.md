## Application Model##

### Property Introspection ###

1. Latest Jenkins Plugin for MyST ensures discovery of *properties* referred in XML(.xml extension) & Properties (.properties extension) file. A property is an expression having following syntax : ***${some.property}***
2. These properties are reported per CI build
3. MyST manages the association between given *version* of an *Artifact* to the properties it refers
4. That said, a property is tracked against the build number. It is possible to know first and last build number a property is introspected along with if it is being reported by *LATEST* build. 
5. For Third Party artifacts, properties are yet not supported

#### Jenkins Console ####

1. Jenkins console will print discovered properties against the file which was introspected, as part of build log
2. 

#### Artifact Property View ####

### Property Registry ###

### Stream Model ###

### Approval / Deployment Behavior ###
