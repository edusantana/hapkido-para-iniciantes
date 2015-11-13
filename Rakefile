desc "Gera epubs do livro"
task :epub

desc "Gera pdf do livro"
task :pdf


EPUB = "hapkido-para-iniciantes.epub"
PDF = EPUB.ext(".pdf")

file EPUB => ["exame-de-faixa.md", "regras-etiquena-no-dojang.md", "metadata.yaml"] do
  system "pandoc -t epub3 -S --toc exame-de-faixa.md regras-etiquena-no-dojang.md metadata.yaml -o hapkido-para-iniciantes.epub"
end

file PDF => ["exame-de-faixa.md", "regras-etiquena-no-dojang.md", "metadata.yaml"] do
  puts PDF
  system "pandoc -s -S --toc exame-de-faixa.md regras-etiquena-no-dojang.md metadata.yaml -o #{PDF}"
end

task :clean do
  rm_rf EPUB
  rm_rf PDF
end

task :epub => EPUB
task :pdf => PDF


task :default => [:clean, EPUB]
