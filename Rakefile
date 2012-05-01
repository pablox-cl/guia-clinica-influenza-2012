# encoding: UTF-8

require 'rake/clean'

EPUB_COVER_IMAGE="--epub-cover-image=images/cover.png"
EPUB_STYLESHEET=
EPUB_METADATA="--epub-metadata=metadata.xml"
OUTPUT="guia_influenza.epub"

desc "Convierte a epub"
task :epub_all do
  system "pandoc -S #{EPUB_METADATA} #{EPUB_COVER_IMAGE} -o #{OUTPUT} title.txt *.markdown"
  system "ebook-viewer #{OUTPUT}"
end

desc "Convierte sólo el capítulo incluído"
task :epub_ch, :number do |t, chapters|
  puts "args are: #{chapters[:number]}"
  system "pandoc -S #{EPUB_METADATA} -o #{chapters[:number]}.epub #{chapters[:number]}*.markdown"
  system "ebook-viewer #{chapters[:number]}.epub"
end

task :default => :epub_all
