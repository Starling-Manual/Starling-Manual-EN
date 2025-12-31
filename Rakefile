require 'fileutils'

REQUIREMENTS = "-r asciidoctor-diagram"
INDEX_FILE = "src/index.adoc"
OUT_FOLDER = "out"

def copy_images_to(out_dir)
  FileUtils.mkdir_p("#{out_dir}/img")
  FileUtils.cp_r("img/.", "#{out_dir}/img")
end

Encoding.default_external = Encoding::UTF_8
Encoding.default_internal = Encoding::UTF_8

task :default => :build_html

desc "Create a multi-page HTML version"
task :build_html do
  out_dir = "#{OUT_FOLDER}/html"
  sh "asciidoctor -r asciidoctor-multipage " +
     "-b multipage_html5 #{REQUIREMENTS} " +
     "-D #{out_dir} -a imagesdir=img " +
     "-o index.html #{INDEX_FILE}"

  copy_images_to(out_dir)
end

desc "Create a single-page HTML version"
task :build_html_single do
  out_dir = "#{OUT_FOLDER}/html-single"
  sh "asciidoctor -b html5 #{REQUIREMENTS} " +
     "-D #{out_dir} -a imagesdir=img " +
     "-o index.html #{INDEX_FILE} "

  copy_images_to(out_dir)
end

desc "Create a PDF version"
task :build_pdf do
  sh "asciidoctor-pdf #{REQUIREMENTS} " +
     "-D #{OUT_FOLDER} " +
     "-o manual.pdf #{INDEX_FILE}"
end

desc "Remove all output files"
task :clean do
  Dir["#{OUT_FOLDER}/*"].each do |f|
    FileUtils.remove_entry(f)
  end
end
