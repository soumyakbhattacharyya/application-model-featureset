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
2. In following screenshot, Properties section shows all existing and past properties associated with an Artifact version. First and Last Build columns next to a property signifies first build number, when CI server reported this property while last build number signifies last time it was posted to MyST. That said, *LATEST* signifies that the property has been reported in recent most build for the artifact version. So effectively properties which *has a specific Last Build entry* are not in use as of now. These properties  which has reached end of life can get reported again and they will show up in this view along with previous entry (ies). But quite obviously, those entries will have *First Build* number and *LATEST* on Last Build column
<p align="center">
  <img src="https://github.com/soumyakbhattacharyya/application-model-featureset/blob/master/artifact-properties-view.jpg" width="800" height="400"/>
  <p align="center">Properties associated with an artifact version</p>
</p>

#### Stream Model

1. Stream consists of Application Blueprint Version(s). Application Blueprint Version in turn consists of Artifact Version(s). Stream Model is a collection of ALL properties required by ALL artifacts consolidating constituent Application Blueprint Version(s). Stream Model is the container where user provides value for the properties. If the properties have default value configured, those values are being used by default, user may override these entries (which are default populated) though. Properties in a stream model can refer other properties. Note that, these properties are being tracked at Platform Instance level. This statement will have significance when we explain property value resolution behavior in more detail in subsequent sections.
2. Stream Model can be edited via the cog wheel that appear in the juncture of a stream & a stage. That said, editing can be done irrespective of the fact that corresponding Release Pipeline is active / inactive. Point to note here is, in inactive state, Stream definition is being considered, to identify properties required by the Stream, while in active state, latest Stream Revision is what is negotiated to discover properties required by the Stream.
3. Stream Model can be saved multiple times without any eventual after effect. However committing Stream Model, creates a potential new  revision / snapshot. If the committed properties affect any other Streams (across Release Pipelines), for all Stages the Stream (or revisions)   

### Approval / Deployment Behavior
