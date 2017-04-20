## Application Model

### Property Introspection

1. Latest Jenkins Plugin for MyST ensures discovery of *properties* referred in XML(.xml extension) & Properties (.properties extension) file. A property is an expression having following syntax : ***${some.property}***
2. These properties are reported per CI build
3. MyST manages the association between given *version* of an *Artifact* to the properties it refers
4. That said, a property is tracked against the build number. It is possible to know first and last build number a property is introspected along with if it is being reported by *LATEST* build. 
5. For Third Party artifacts, properties are yet not supported

#### Jenkins Console

1. Jenkins console will print discovered properties against the file which was introspected, as part of build log
2. In following screenshot section (A) highlights *customProperties* discovered during the build process and section (B) highlights files which were introspected 
<p align="center">
  <img src="https://github.com/soumyakbhattacharyya/application-model-featureset/blob/master/jenkins-console.jpg" width="500" height="600"/>
  <p align="center">Jenkins Console</p>
</p>  


#### Property Registry

1. Properties that are reported gets registered in MyST
2. MyST tracks version of artifact to which the properties are associated and vice versa
3. In following screenshot typical view of Property Registry is shown. Via this UI, user can
	1. Provide a meaningful description & default value for the property
	2. View all artifacts which are associated with *a specific* property 
<p align="center">
  <img src="https://github.com/soumyakbhattacharyya/application-model-featureset/blob/master/property-registry-list-view.jpg" width="800" height="200"/>
  <p align="center">List of Property Registry Entries</p>
</p>
<p align="center">
  <img src="https://github.com/soumyakbhattacharyya/application-model-featureset/blob/master/property-registry-artifact-view.jpg" width="800" height="200"/>
  <p align="center">Artifacts associated with a property</p>
</p>

#### Artifact Property View

1. While Property Registry depicts the relationship between a property to ALL artifacts it relates to, this view shows the opposite i.e. it shows, all properties that a given version of artifact associates with 
2. In following screenshot 
<p align="center">
  <img src="https://github.com/soumyakbhattacharyya/application-model-featureset/blob/master/artifact-properties-view.jpg" width="800" height="400"/>
  <p align="center">Properties associated with an artifact version</p>
</p>

### Stream Model

### Approval / Deployment Behavior
