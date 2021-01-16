require 'rake/clean'
# rake/clean définit CLEAN (Rake::FileList) pour les fichiers temporaires
# et CLOBBER (Rake::FileList) pour les fichiers de sortie

chapters = %w[intro rdd sql] # %w définit un tableau de chaînes

# Array : https://ruby-doc.org/core-trunk/Array.html
# Rake::FileList : http://ruby-doc.org/stdlib-trunk/libdoc/rake/rdoc/Rake/FileList.html
chapter_files = Rake::FileList[chapters.map{|c| "#{c}/#{c}.adoc"}]
fig_dirs = Rake::FileList[chapters.map{|c| "#{c}/figs"}]

desc "Génère la version livre et la version slides"
task :default => [:generate_book]
# :default est un symbole Ruby
# task <cible> => <dépendances>

desc "Initialise le répertoire des images"
directory "html/figs" => "html" do
    mkdir_p "html/figs"
    cp Dir["figs/*.png", "figs/*.svg"], "html/figs"
    fig_dirs.each do |d|
        cp Dir["#{d}/*.png", "#{d}/*.svg"], "html/figs"
    end
end

desc "Répertoire de destination des fichiers html"
directory "html"

# ajoute le répertoire html comme fichier de sortie
CLOBBER << "html"

desc "Génère la version livre du cours"
task :generate_book => %w[html/index.html]

file "html/index.html" => ["html", "html/figs", "index.adoc"] + chapter_files do
    sh "asciidoctor -r asciidoctor-diagram -D html/ index.adoc"
end
