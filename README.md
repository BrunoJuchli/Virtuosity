## This is an add-in for [Fody](https://github.com/Fody/Fody/) 

Change all members to `virtual` as part of your build.

[Introduction to Fody](http://github.com/Fody/Fody/wiki/SampleUsage)

## Nuget package http://nuget.org/packages/Virtuosity.Fody 

What it actually does to your assembly

### Selects all members that meet the following criteria
  * from non `sealed` classes
  * non `static` members
  * non `abstract` members
  * non `private` members
  * non `virtual` members

### Change them to `virtual`
### For all (now `virtual`) members 
  * change calls to those members to `virtual`
  * change `new` modifiers to `override` modifiers

# Why is this useful

If you are coding in .net you will have used or heard of one of the following tools

 * [NHibernate](http://community.jboss.org/wiki/NHibernateforNET)
 * [Rhino Mocks](http://ayende.com/projects/rhino-mocks.aspx)
 * [Moq](http://code.google.com/p/moq/)
 * [NMock2](http://sourceforge.net/projects/nmock2/)
 * [Ninject](http://ninject.org/)
 * [NSubstitute](http://nsubstitute.github.com/)
 * [Entity Framework](http://www.asp.net/entity-framework/)

Well all these tools make use of [DynamicProxy](http://www.castleproject.org/projects/dynamicproxy/). DynamicProxy allows for runtime interception of members. The one caveat is that all intercepted members must be virtual. This means that that all the above tools, to some extent, require members to be virtual.

 * [http://msdn.microsoft.com/en-us/library/gg715120(v=vs.103).aspx] "One of the requirements for lazy loading proxy creation is that the navigation properties must be declared virtual"
 * [Must Everything Be Virtual With NHibernate?](http://davybrion.com/blog/2009/03/must-everything-be-virtual-with-nhibernate/)
 * [RhinoMocks Why methods need to be declared virtual](http://groups.google.com/group/RhinoMocks/browse_thread/thread/a2cb93f1ba8d4735/37d377ddb92cb729?lnk=gst&q=virtual)
 * [http://groups.google.com/group/moqdisc/browse_thread/thread/2e02e367d017f274 Moq My method needs to be virtual?]
 * ["NMock supports mocking of classes with virtual methods"](http://www.nmock.org/nmock1-documentation.html)
 * [Ninject Important Note:Your methods/properties to be intercepted must be virtual!](http://innovatian.com/2010/03/using-ninject-extensions-interception-part-1-the-basics/)
 * [NSubstitute:Some operations on non virtual members should throw an exception](http://groups.google.com/group/nsubstitute/browse_thread/thread/407cb0408ce97bfd)

If you forget to mark something as virtual these tools will not work and fail in sometimes very unhelpful ways. So rather than having to remember to mark things as virtual Virtuosity means members will be virtual by default.
