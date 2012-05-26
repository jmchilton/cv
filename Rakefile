require 'rake/clean'

CLEAN.include('build')
TITLE='chilton'

task :default => [:build_all]

directory "build" 

def build(type, is_resume)
  directory="build/#{type}"
  sh "mkdir -p #{directory}"
  sh "cat source.tex | sed -e 's/IS_RESUME/#{is_resume}/' > #{directory}/#{TITLE}.tex"
  sh "pdflatex -output-directory #{directory} #{directory}/#{TITLE}.tex"
end

def view_pdf(type)
  sh "evince build/#{type}/#{TITLE}.pdf"
end

task :build_resume => ["build"] do
  build(:resume, "true")
end

task :build_cv => ["build"] do
  build(:cv, "false")
end

task :build_all => [:build_resume, :build_cv] do
end

task :cv => [:build_cv] do
  view_pdf(:cv)
end

task :resume => [:build_resume] do
  view_pdf(:resume)
end


