# THINGS IN HERE

## GEMS

```
gem "sassc-rails"
gem 'simple_form'
gem 'haml'
gem 'bootstrap-sass'
```
- i didnt use bootstrap sass
- sass rails for .scss files

## MODELS
- categories have many jobs
- jobs belong to category

## OTHER
- did his own styling
- filtering the navbar based on the categories

```
	def index
		if params[:category].blank?
			@jobs = Job.all.order("created_at DESC")
		else
			@category_id = Category.find_by(name: params[:category]).id
			@jobs = Job.where(category_id: @category_id).order("created_at DESC")
		end
	end

-- and the link on the navbar, passing it the category
	- Category.all.each do |category|
		%li= link_to category.name, jobs_path(category: category.name)
```
