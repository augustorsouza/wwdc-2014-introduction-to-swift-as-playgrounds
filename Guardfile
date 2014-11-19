guard :shell do
  watch(/(.*).md/) do |m| 
    puts
    puts
    puts
    puts "Running #{m[0]}"
    puts `playground #{m[0]}`
  end
end