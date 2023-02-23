# Clean Architecture
- A Craftsman's Guide to Software Structure and Design
- Author: Robert C. Martin


## Chapter Summaries



### DIP (Dependencies Inversion Principle)
- 87pg - 91pg

The basic idea is that we want to limit the volitility of our codebase. As developers we control our code but we can not controll external libraries/dependecies. 
So the author recommends that limit our use of concrete class and modules in our code. Concrete intities are defined as anything that is implimented as it is declared. 
Instead the author proposes that use `Abstract` classes or `interfaces` as an intermediate layer between our code and the volitile code. A good example is `SpringBoot` API definition structure or the `Google Drive API` wrapper build by me at `Argo AI`. 
The author recognizes that some classes cannot be avoided like the `String` class in java. The purpose of the principle is to reduce the number of instance where we directly interact with volite classes as much as possible.


### Chapter 12: Components
- 95pg - 102pg
The chapter zeros in on the history of components, walking back our step to the current point in time. The author explained that old programs were first loaded in memory and required multiple passed to be loaded, because `RAM` was limied. In the multiple passes the binaray were first loaded in to the slow disk and then loaded into the cpu. The 0000-1777 registers were all given to application code and 2000-47777 was given to function code or componets/function. As time when on, the application code grew si tget added 5000-6777 regsiters to the application space. Now the function code was growing beyond the defined space. This lead to relocatable binaries and a loader. The loader would load binaries when and if tehy were needed. Next came the linker which would resolved the reference once loading loaction had been defined. They worked for a while, but compile times grew to hours, and linking became a bottleneck. To make it more fisable they seperated the two steps. As `Moore Law` took prevelence CPU clock speed when from KH to MH and RAM from Kb to Mb. The improvement in technologies make linking and loading possible.

