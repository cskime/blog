source "https://rubygems.org"

# Match GitHub Pages' Jekyll environment for local development.
gem "github-pages", group: :jekyll_plugins

group :jekyll_plugins do
  gem "jekyll-include-cache"
end

# Required for `bundle exec jekyll serve` on Ruby 3+.
gem "webrick", "~> 1.8"

platforms :windows, :jruby do
  gem "tzinfo", ">= 1", "< 3"
  gem "tzinfo-data"
end
