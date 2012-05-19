# encoding: UTF-8

require 'rake/clean'

EPUB_COVER_IMAGE="--epub-cover-image=images/cover.png"
EPUB_STYLESHEET="--epub-stylesheet=styles/style.css"
EPUB_METADATA="--epub-metadata=metadata.xml"
EPUB_EMBED_FONT="--epub-embed-font=styles/fonts"
FONTS=["gobCL_Regular.otf", "gobCL_Bold.otf", "gobCL_Light.otf", "gobCL_Heavy.otf"]
OUTPUT="guia_influenza.epub"

def embed_fonts
  FONTS.collect! do |font|
    EPUB_EMBED_FONT + "/" + font
  end
  FONTS.join " "
end

desc "Convierte a epub"
task :epub_all do
  system "pandoc -S --table-of-contents #{EPUB_METADATA} #{EPUB_COVER_IMAGE} #{EPUB_STYLESHEET} #{embed_fonts} -o #{OUTPUT} title.txt *.markdown"
  system "ebook-viewer #{OUTPUT}"
end

desc "Convierte sólo el capítulo incluído"
task :epub_ch, :number do |t, chapters|
  puts "args are: #{chapters[:number]}"
  system "pandoc -S #{EPUB_METADATA} -o #{chapters[:number]}.epub #{chapters[:number]}*.markdown"
  system "ebook-viewer #{chapters[:number]}.epub"
end

task :default => :epub_all
