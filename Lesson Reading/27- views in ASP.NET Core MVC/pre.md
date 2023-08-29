# Views in ASP.NET Core MVC

In the Model-View-Controller (MVC) pattern, the view handles the app's data presentation and user interaction. A view is an HTML template with embedded Razor markup.

## Layouts

Use layouts to provide consistent webpage sections and reduce code repetition. Layouts often contain the header, navigation and menu elements, and the footer.

## Partial Views

Partial views reduce code duplication by managing reusable parts of views. For example, a partial view is useful for an author biography on a blog website that appears in several views.

## View components

View components are similar to partial views in that they allow you to reduce repetitive code, but they're appropriate for view content that requires code to run on the server in order to render the webpage. View components are useful when the rendered content requires database interaction, such as for a website shopping cart.

## Benefits of using views

- The app is easier to maintain because it's better organized. Views are generally grouped by app feature. This makes it easier to find related views when working on a feature.
- The parts of the app are loosely coupled. You can build and update the app's views separately from the business logic and data access components. You can modify the views of the app without necessarily having to update other parts of the app.
- It's easier to test the user interface parts of the app because the views are separate units.
- Due to better organization, it's less likely that you'll accidentally repeat sections of the user interface.

***the article goes on to talk about how to create a new view and the return data type for controllers using views***

## creating forms in ASP.NET MVC

## FORMS – WEAKLY TYPED

This is the easiest and quickest way to create forms in MVC.

1. Go to Views Home Index.cshtml and update it with following code.

        <h4 style="color:purple">
        <b>ID:</b>    @ViewBag.ID <br />
        <b>Name:</b>  @ViewBag.Name <br />
        <b>Addon:</b> @ViewBag.Addon
        </h4>
        <hr />
        <h3><b>Forms: Weakly Typed</b></h3>
        
        <form action="form1" method="post">
            <table>
                <tr>
                    <td>Enter ID: </td>
                    <td><input type="text" name="txtId" /></td>
                </tr>
                <tr>
                    <td>Enter Name: </td>
                    <td><input type="text" name="txtName" /></td>
                </tr>
                <tr>
                    <td>Addon: </td>
                    <td><input type="checkbox" name="chkAddon" /></td>
                </tr>
                <tr>
                    <td colspan="2"><input type="submit" value="Submit  Form" /></td>
                </tr>
            </table>
        </form>
2. Now, add an action method for this form in HomeController.cs

        [HttpPost]
        public ActionResult form1(int txtId, string txtName, string chkAddon)
        {
            ViewBag.Id = txtId;
            ViewBag.Name = txtName;
            if (chkAddon != null)
                ViewBag.Addon = "Selected";
            else
                ViewBag.Addon = "Not Selected";
 
            return View("Index");
        }

### output

![h](https://www.completecsharptutorial.com/wp-content/uploads/2017/11/New-Picture-1-2.png)

## STRONGLY TYPED

In this method, we send objects (model) instead of sending each item as parameter. It is easy to maintain because you don't need to remember each input item and IntelliSense will show you automatically the each item.

Intellisense Help
Step 1: Go to Index.cshtml and update the code like this.

    @model MvcForms.Models.StudentModel
    <h4 style="color:purple">
    <b>ID:</b>    @ViewBag.ID <br />
    <b>Name:</b>  @ViewBag.Name <br />
    <b>Addon:</b> @ViewBag.Addon
    </h4>
    <hr />
    <h3><b>Forms: Strongly Typed</b></h3>
    
    @using (Html.BeginForm("Form2", "Home", FormMethod.Post))
    { 
        <table>
            <tr>
                <td>Enter ID: </td>
                <td>@Html.TextBoxFor(m => m.Id)</td>
            </tr>
            <tr>
                <td>Enter Name: </td>
                <td>@Html.TextBoxFor(m => m.Name)</td>
            </tr>
            <tr>
                <td>Addon: </td>
                <td>@Html.CheckBoxFor(m => m.Addon)</td>
            </tr>
            <tr>
                <td colspan="2"><input type="submit" value="Submit Form" /></td>
            </tr>
        </table>
    Step 2: Go to HomeController.cs and add the following action method.
    [HttpPost] 
            public ActionResult Form2(Models.StudentModel sm)
            {
                ViewBag.Id = sm.Id;
                ViewBag.Name = sm.Name;
                if (sm.Addon == true)
                    ViewBag.Addon = "Selected";
                else
                    ViewBag.Addon = "Not Selected";

                return View("Index");
            }

## STRONGLY TYPED AJAX (ASYNCHRONOUS)

Asynchronous AJAX form is a very magical way to submit data to the controller without happening page load. Asynchronous AJAX Forms simply post back the data to the controllers and update the only that part of the page, which has to display output.

To make this happen, we will use JQuery-Unobstrusive-AJAX. This is a great feature which is launched in MVC 3. It helps you to create AJAX Form without writing bunch of javascript code. Before creating Asynchronous AJAX Form you need to add JQuery-Unobstrusive-AJAX in your project. Adding is very easy, and just follows the steps.

Adding JQuery-Unobstrusive-AJAX
Step 1: Right-click on your Project name in Solution Explorer and click Manage Nuget Packages…
Step 2: Go to Browse and search for ajax. Find and Install Microsoft-JQuery-Unobstrusive-Ajax.
Installing AJAX
Step 3: After installing this you can see it in Script folder.
JQuery-plugin
Now, your project is ready to use JavaScript and AJAX.

Create Forms and Controller.
Step 1: Create Form in Index.cshtml

    @model MvcForms.Models.StudentModel
    <script src="@Url.Content("~/Scripts/jquery-1.10.2.min.js")" type="text/javascript"></script>
    <script src="@Url.Content("~/Scripts/jquery.unobtrusive-ajax.js")" type="text/javascript"></script>
    
    <h4 id="id1" style="color:purple"></h4>
    <hr />
    <h3><b>Forms - Strongly Typed AJAX (Asynchronous)</b></h3>
        @using (Ajax.BeginForm("Form3", "Home", new AjaxOptions
        {
            HttpMethod = "POST",
            UpdateTargetId = "id1",
            LoadingElementId = "LoadingImage",
            OnSuccess = "onSuccess_Message",
            OnFailure="onFailure_Message"
            
        }))
        {
            <table>
                <tr>
                    <td>Enter ID: </td>
                    <td>@Html.TextBoxFor(m => m.Id)</td>
                </tr>
                <tr>
                    <td>Enter Name: </td>
                    <td>@Html.TextBoxFor(m => m.Name)</td>
                </tr>
                <tr>
                    <td>Addon: </td>
                    <td>@Html.CheckBoxFor(m => m.Addon)</td>
                </tr>
                <tr>
                    <td colspan="2"><input type="submit" value="Submit Form" /></td>
                </tr>
            </table>
            <div id="LoadingImage" style="display:none">Loading...</div>
            <div id="onSuccess_Message"></div>
            <div id="onFailure_Message"></div>
        }

Step 2: Go to HomeController and add the following action method.

    [HttpPost] 
            public ActionResult Form3(Models.StudentModel sm)
            {
                if(ModelState.IsValid)
                {
                    System.Text.StringBuilder sb = new System.Text.StringBuilder();
                    sb.Append("ID: " + sm.Id + "<br />");
                    sb.Append("Name: " + sm.Name + "<br />");
                    sb.Append("Addon: " + sm.Addon + "<br />");
                    return Content(sb.ToString());
                }
                else
                {
                    return View("Index");
                }            
            }

## PURE HTML FORMS WITH AJAX AND JQUERY

In this method, you can not only send data from input controls but can also use html elements like < p>…< /p>, < span>…< /span> to send data to controllers. This is pure JQuery and AJAX query.

Create Forms
Step 1. Go to Index.cshtml and create form like this.

    <h3><b>Forms - Pure HTML and JQUERY</b></h3>
    
        <table>
            <tr>
                <td>Enter ID: </td>
                <td><input type="text" id="Id" /></td>
            </tr>
            <tr>
                <td>Enter Name: </td>
                <td><input type="text" id="Name" /></td>
            </tr>
            <tr>
                <td>Addon: </td>
                <td><input type="checkbox" id="Addon" /></td>
            </tr>
            <tr>
                <td colspan="2"><button onclick="submit()">Submit Form</button></td>
            </tr>
        </table>
    
    <h4 style="color:purple" id="output"></h4>
    
    <script src="~/Scripts/jquery-1.10.2.min.js" type="text/javascript"></script>
    <script>
        function submit(){
            var data = {
                Id: $('#Id').val(),
                Name: $('#Name').val(),
                Addon: $('#Addon').is(':checked')
            };
    
            $.post("/Home/Form4", { sm: data }, function () { alert('Successfully Saved') });
        }
    </script>
    Step 2: Go to HomeController and add following action method.
    [HttpPost] 
            public ActionResult Form4(StudentModel sm)
            {
                string value = "ID: "+ Convert.ToString(sm.Id) 
                    + "<br />Name: " + sm.Name 
                    + "<br />Addon: " + Convert.ToString(sm.Addon);
    
                string s = "$('#output').html('" + value + "');";
                return JavaScript(s);
            }

## SUMMARY

In this tutorial, you learned 4 different ways to create form and submit data to the controller. All these 4 ways used widely in MVC and I hope now you will be able to create a form in ASP.NET MVC. In the next chapter, you will learn FormCollection object in details with programming example. FormCollection objects make a job much easier when collecting form data into the controller.
