!SLIDE 
# Organizing Test Helpers in Rails #

!SLIDE bullets
# Helpers #

* config/initializers vs. config/application.rb
* spec/support vs. spec/spec_helper.rb
* features/support vs. features/env.rb

!SLIDE
# RSpec
spec/support/resque_spec.rb
    @@@ruby
    RSpec.configure do |config|
      config.before do
        ResqueSpec.reset!
      end
    end

!SLIDE
# Cucumber
features/support/authentication_helper.rb
    @@@ruby
    module AuthenticationHelper
      def sign_in_admin(admin)
        visit '/admins/sign_in'
        fill_in 'Email', with: admin.email
        fill_in 'Password', with: admin.password
        click_button 'Sign in'
      end
    end

    World AuthenicationHelper

!SLIDE bullets
# Done #
* Stop polluting spec_helper.rb and env.rb
* Don't even add a 1-line require in there
* Many small files are better than one
