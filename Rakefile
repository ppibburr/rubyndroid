desc "Removes generated classes and apk's"
task :clean do
  sh "ant clean"
end

desc "Compiles classes and builds DEBUG apk file"
task :debug do
  sh "cp -rf ../jamruby/assets/* assets/" 
  sh "ant debug"
end

desc "Installs to a device/emulator"
task :install do
  sh "adb uninstall org.jamruby.runner"
  sh "adb install -r bin/*debug.apk"
end

desc "Runs the app on the device/emulator"
task :run do
  sh "adb shell am force-stop org.jamruby.runner && adb shell monkey -p org.jamruby.runner 1"
end

desc "Clean, create debug apk, install apk, push ruby file, run's the app"
task :all => [:clean, :debug, :install, :run] do
  
end

desc "Take a screenshot"
task :screenshot do
  sh "adb shell screencap -p /sdcard/screen.png"
  sh "adb pull /sdcard/screen.png"
  sh "adb shell rm /sdcard/screen.png"
end

task :default => :all
