require 'fileutils'

REQUIREMENTS = "-r asciidoctor-diagram"
MANUAL_INDEX = "src/index.adoc"
OUT_FOLDER = "out"

PIWIK_TRACKING_CODE = %(<!-- Piwik -->
<script type="text/javascript">
  var _paq = _paq || [];
  _paq.push(["setDomains", ["*.manual.starling-framework.org"]]);
  _paq.push(['trackPageView']);
  _paq.push(['enableLinkTracking']);
  (function() {
    var u="//analytics.gamua.com/";
    _paq.push(['setTrackerUrl', u+'piwik.php']);
    _paq.push(['setSiteId', '9']);
    var d=document, g=d.createElement('script'), s=d.getElementsByTagName('script')[0];
    g.type='text/javascript'; g.async=true; g.defer=true; g.src=u+'piwik.js'; s.parentNode.insertBefore(g,s);
  })();
</script>
<noscript><p><img src="//analytics.gamua.com/piwik.php?idsite=9" style="border:0;" alt="" /></p></noscript>
<!-- End Piwik Code -->)

def insert_tracking_code(filename)
  text = File.read(filename)
  unless text.include? "<!-- Piwik -->"
    text.gsub!("</head>", PIWIK_TRACKING_CODE + "\n</head>")
    File.open(filename, "w") {|file| file.puts text }
  end
end

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
