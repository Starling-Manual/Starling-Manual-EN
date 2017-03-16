require 'fileutils'

REQUIREMENTS = "-r asciidoctor-diagram"
MANUAL_INDEX = "src/index.adoc"
OUT_FOLDER = "out"

task :default => :build_html

desc "Create the HTML manual"
task :build_html do
  sh "asciidoctor -b html5 #{REQUIREMENTS} -D #{OUT_FOLDER} -o manual.html #{MANUAL_INDEX}"
end

desc "Create a PDF version of the manual"
task :build_pdf do
  sh "asciidoctor-pdf #{REQUIREMENTS} -D #{OUT_FOLDER} -o manual.pdf #{MANUAL_INDEX}"
end

desc "Create an EPUB version of the manual"
task :build_epub do
  sh "asciidoctor-epub3 #{REQUIREMENTS} -D #{OUT_FOLDER} -o handbook.ebpub #{MANUAL_INDEX}"
end

desc "Remove all output files"
task :clean do
  Dir["#{OUT_FOLDER}/*"].each do |f|
    FileUtils.remove_entry(f)
  end
end
