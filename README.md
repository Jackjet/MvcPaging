The MvcPaging library contains an ASP.NET MVC HTML helper that renders a pager based on given parameters.
A live demo can be found at http://demo.taiga.nl/mvcpaging.

Usage (Razor / pseudo code): 
    
    @Html.Pager(pageSize, pageNumber, totalItemCount)

Options are added via the Options method:

	@Html.Pager(pageSize, pageNumber, totalItemCount).Options(o => o
		.Action("action")
		.AddRouteValue("q", mySearchQuery)
	)

Possible options:
	Action(string action)
		Sets an alternative action for the pager that is different from the current action

	AddRouteValue(string name, object value)
		Adds a single route value parameter that is added to page url's

	AddRouteValueFor<TProperty>(Expression<Func<TModel, TProperty>> expression)
		Adds a strongly typed route value parameter based on the current model
		(e.g. AddRouteValueFor(m => m.SearchQuery))

	RouteValues(object routeValues)
		Adds route value parameters that are added to the page url's

	RouteValues(RouteValueDictionary routeValues)
		Adds route value parameters that are added to the page url's

	DisplayTemplate(string displayTemplate)
		When set, the internal HTML rendering is bypassed and a DisplayTemplate view with the given
        name is rendered instead. Note that the DisplayTemplate must have a model of type PaginationModel

	MaxNrOfPages(int maxNrOfPages)
		Sets the maximum number of pages to show	
	
	AlwaysAddFirstPageNumber
		By default we don't add the page number for page 1 because it results in canonical links. 
		Use this option to override this behaviour.	

	PageRouteValueKey
		Set the page routeValue key for pagination links

	SetPreviousPageText
		Set a custom text for the previous page

	SetNextPageText
		Set a custom text for the next page

--------------------------------------------------------------------------------------------------------

The library contains a PagedList class that makes it easy to work with paged data. Use it via an 
extension method on IEnumerable<> or IList<>:

    myList.ToPagedList(pageIndex, pageSize)

with any unpaged list or 

    myList.ToPagedList(pageIndex, pageSize, totalItemCount)

when the list already only contains the data for the page

--------------------------------------------------------------------------------------------------------

For the source and a demo project, see https://github.com/martijnboland/MvcPaging. 

###Contributing

We accept contributions via GitHub pull requests. Please use tabs for indentation.
