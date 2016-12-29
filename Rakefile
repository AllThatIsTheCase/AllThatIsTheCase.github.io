task :default => Dir['*.mdt'].collect{|mdt| mdt.sub(/t$/, '')} do
end

rule '.md' => '.mdt' do |t|
  begin
    open(t.name, 'w'){|md|
      IO.readlines(t.source).each{|line|
        line = line.gsub('[ ]', '<input disabled type="checkbox">').gsub(/\[x\]/i, '<input disabled checked type="checkbox">')
        line += '  ' if line =~ /"checkbox"/ && line !~ /  $/
        md.write(line)
      }
    }
  rescue
    File.unlink(t.name)
  end
end
