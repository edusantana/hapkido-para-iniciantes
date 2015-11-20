desc "Gera epubs do livro"
task :epub

desc "Converte imagens svg para pdf para criar documetno com latex"
task :svg2pdf

desc "Gera pdf do livro"
task :pdf => :svg2pdf

desc "Checa se o livro produzido está em conformidade com o formato epub"
task :check



EPUB = "hapkido-para-iniciantes.epub"
PDF = EPUB.ext(".pdf")

file EPUB => ["exame-de-faixa.md", "regras-etiquena-no-dojang.md", "metadata.yaml"] do
  system "pandoc -t epub3 -S --toc exame-de-faixa.md regras-etiquena-no-dojang.md metadata.yaml -o hapkido-para-iniciantes.epub"
end

file PDF => ["exame-de-faixa.md", "regras-etiquena-no-dojang.md", "metadata.yaml"] do
  puts PDF
  system "pandoc -s -S --toc exame-de-faixa.md regras-etiquena-no-dojang.md metadata.yaml -o #{PDF} --latex-engine=xelatex"
end

task :check => EPUB do
    system "java -jar /home/eduardo/programas/book/epubcheck-4.0.1/epubcheck.jar #{EPUB}"
end

FileList.new('media/*.svg').each do |svg|
  file "#{svg}.pdf" => svg do
    system "inkscape -D -z --file=#{svg} --export-pdf=#{svg}.pdf"
  end
  task :svg2pdf => "#{svg}.pdf"
end


task :clean do
  rm_rf EPUB
  rm_rf PDF
end

task :epub => EPUB
task :pdf => PDF


task :default => [:clean, :epub, :pdf]
