require 'fileutils'

REQUIREMENTS = "-r asciidoctor-diagram"
INDEX_FILE = "src/index.adoc"
OUT_FOLDER = "out"

Encoding.default_external = Encoding::UTF_8
Encoding.default_internal = Encoding::UTF_8

task :default => :build_html

desc "Create a multi-page HTML version"
task :build_html do
  sh "asciidoctor -r asciidoctor-multipage " +
      "-b multipage_html5 #{REQUIREMENTS} " +
      "-D #{OUT_FOLDER}/html -a data-uri " +
      "-o index.html #{INDEX_FILE}"
end

desc "Create a single-page HTML version"
task :build_html_single do
  sh "asciidoctor -b html5 #{REQUIREMENTS} -D #{OUT_FOLDER} -o manual.html #{INDEX_FILE} "
end

desc "Create a PDF version"
task :build_pdf do
  sh "asciidoctor-pdf #{REQUIREMENTS} -D #{OUT_FOLDER} -o manual.pdf #{INDEX_FILE}"
end

desc "Remove all output files"
task :clean do
  Dir["#{OUT_FOLDER}/*"].each do |f|
    FileUtils.remove_entry(f)
  end
end
