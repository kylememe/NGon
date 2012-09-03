Usage:

The first thing you need to do when using NGon, is to add the NGonActionFilterAttribute to the global action filters:

Global.asax.cs
protected void Application_Start()
{
	AreaRegistration.RegisterAllAreas();

	GlobalFilters.Filters.Add(new NGonActionFilterAttribute());

	RegisterGlobalFilters(GlobalFilters.Filters);
	RegisterRoutes(RouteTable.Routes);
}

Then, in your controller, you can add any value to the dynamic NGon property of the ViewBag:

public class HomeController : Controller
{
    public ActionResult Index()
    {
        ViewBag.NGon.SomeValue = 100;
        return View();
    }
}

 In your HTML, you then add this (you'll likely want to put this in your layout/master page file):
@Html.IncludeNGon()

 Finally, anywhere in your javascript, you now have access to that value:
<script type="text/javascript">
    $(function () {
        $("#button").click(function () {
            alert(ngon.SomeValue);
        });
    }); </script>
