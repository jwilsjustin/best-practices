##### Rails example that illustrates using a `before_action` to set the current user to an instance variable `@current_user`

```ruby
class ApplicationController < ActionController::Base
  
  helper_method :current_user
  before_action :current_user

  def current_user
    if Digest::SHA256.hexdigest("app_salt" + "user_salt"  + "auth_token") == cookies[:sso_token]
      @current_user ||= User.where(auth_token: "auth_token")
    end
    @current_user
  end

end
```

When you need to reference the current logged in user in your controller or view, the more efficient way is through the instance variable, `@current_user`. Referencing through the method call `current_user` will run the entire authentication process. Probably multiple times. When you use a `before_action` you can Set It And Forget It™.

Similar to what Devise does
- https://github.com/plataformatec/devise/blob/master/test/rails_app/app/controllers/application_controller.rb#L6
- https://github.com/plataformatec/devise/blob/master/lib/devise/controllers/helpers.rb
