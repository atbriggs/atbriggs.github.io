# Thorfile
require 'thor'
require 'date'
require 'fileutils'

class JekyllCLI < Thor
  desc "new_post TITLE", "Create a new Jekyll post with the given TITLE"
  def new_post(title)
    date = Date.today
    slug = title.downcase.strip.gsub(' ', '-').gsub(/[^\w-]/, '')
    filename = "_posts/#{date}-#{slug}.md"

    if File.exist?(filename)
      puts "A post with this title already exists."
      exit 1
    end

    FileUtils.mkdir_p(File.dirname(filename))

    File.open(filename, 'w') do |file|
      file.puts "---"
      file.puts "layout: post"
      file.puts "title: \"#{title}\""
      file.puts "date: #{date}"
      file.puts "categories: "
      file.puts "---"
    end

    puts "New post created: #{filename}"
  end
end

JekyllCLI.start(ARGV)
