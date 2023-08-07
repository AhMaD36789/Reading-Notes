# pseudo code

1. delete old DB that didnt implement identity
1. delete migrations
1. download Microsoft.ASPNetCore.Identity.EntityFramework
1. add new class to models folder named ApplicationUser
1. ApplicationUser inherits from IdentityUser class (containts base properties)
1. change DBContext to inherit from IdentityDBContext< ApplicationUser> (configures and interacts with DB while implementing identity framework )
1. in override for OnModelCreating add

        base.OnModerCreating(modelbuilder)
1. add migration and update the database
1. register Identity service in program.cs by adding

        builder.servicess.AddIdentity< ApplicationUser, IdentityRole>(options=> 
        {
            options.User.RequireUniqueEmail = true;
        }).AddEntityFreameworkStores<DBContext>();
        //lookup the different options available to customize inside the options
1. add new interface IUser and add new class IdentityUserService that implements the new interface and in program.cs addTransient for the new interface-class
1. interface contains the following

    public task<> Register (RegisterUser RegisterUser)
1. Add new class to configure DTO to take some of the properties added by default in the pre created table (return to lecture 10:45:00 AM - 10:58:00 AM)
1. after implementing the service add new controller and inject the service in the controller
1. inject in IdentityUserService

        private UserManager< ApplicationUser> suerManager;
        public IdentityUserService(UserManager< ApplicationUser> manager){
        userManager = manager;
        }

1. in register method in IdentityUserService (ModelState && ModelStateDictionary)

        Var user = new ApplicationUser()
        {
            UserName = registerUser.Username
            Email = registerUser.Email
            PhoneNumber = registerUser.PhoneNumber
        };
        var result = await userManager.CreateAsync(user, registerUser.Password);
        if (result.Succeeded)
        {
            return new UserDto()
            {
                Id = user.Id,
                Username = user.UserName
            };
        }

        foreach ( var error in result.Errors)
        {
            var error = error.Code.Contains("Password") ? nameof(registerUser.Password):
                        error.Code.Contains("Email") ? NameOf(registerUser.Email):
                        error.Code.Contains("Username") ? NameOf(registerUser.Username):
                        "";
            modeState.AddModelError(errorKey, error.Description);
        }

        return;

1. in controller

        var user = await userService.Register(data, this.ModelState);
        if (ModeState.isValid)
        return user;
        return BadRequest(new ValidationProblemDetails(ModelState));
1. add ModelStateDictionary ModelState as a param to the interface and the service and send it from the controller to the service

1. sometimes there is a memory error program needs to be reset to automatically resolve
1. 11:56:00 AM login service
