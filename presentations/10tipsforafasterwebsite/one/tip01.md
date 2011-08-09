!SLIDE bullets incremental
.notes  werkt wel (wel pre-combinen graag! deploy-taak)
# Tip 1 #
## Asset combination ##

!SLIDE 
#Jammit#
	@@@ruby
		#Gemfile
		gem "jammit"
		
		# Rakefile
		Jammit.package!
		
		# Capfile
		$ jammit --force

!SLIDE veel-code
#rack-pagespeed#

	
	@@@ruby
	config.middleware.use Rack::PageSpeed, :public => Rails.public_path do
		store :disk => Dir.tmpdir # require 'tmpdir'
		inline_javascript :max_size => 4000
		inline_css
		combine_javascripts
	end
	# https://rubygems.org/gems/rack-pagespeed
	
!SLIDE
#Sprites#
##Rails 3.1##
	
!SLIDE
#Other?#