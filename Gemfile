source "https://rubygems.org"

# Jekyll 版本
gem "jekyll", "~> 4.3.0"

# GitHub Pages 兼容
gem "github-pages", group: :jekyll_plugins

# 主题
gem "minima", "~> 2.5"

# 插件
group :jekyll_plugins do
  gem "jekyll-feed", "~> 0.12"
  gem "jekyll-sitemap"
  gem "jekyll-seo-tag"
  gem "jekyll-last-modified-at"
end

# Windows 和 JRuby 不包含 zoneinfo 文件，需要 tzinfo-data gem
platforms :mingw, :x64_mingw, :mswin, :jruby do
  gem "tzinfo", ">= 1", "< 3"
  gem "tzinfo-data"
end

# 性能提升（JRuby 用户）
gem "http_parser.rb", "~> 0.6.0", :platforms => [:jruby]

# Windows 用户需要 wdm
gem "wdm", "~> 0.1.1", :platforms => [:mingw, :x64_mingw, :mswin] 