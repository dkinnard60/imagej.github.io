---local player = game.Players.LocalPlayer
local character = player.Character
local localroot = character:WaitForChild("HumanoidRootPart")
local function closest()
    local range = 50
    local target = nil
    for _, v in pairs(game.Players:GetPlayers()) do
        if v ~= player and v.Character and not v.Character:FindFirstChildWhichIsA("ForceField") then
            local JN = v.Character:FindFirstChild("HumanoidRootPart")
            local JNR = v.Character:FindFirstChildOfClass("Humanoid")
            if JN and JNR.Health > 0 then
                local dist = (localroot.Position - JN.Position).magnitude
                if dist < range then
                    range = dist
                    target = v.Character
                end
            end
        end
    end
    return target
end
game.Players.LocalPlayer.CharacterAdded:Connect(function(char)
    character = char
    localroot = character:WaitForChild("HumanoidRootPart")
end)
local jh = closest()
game:GetService("RunService").Heartbeat:Connect(function()
    jh = closest()
end)
while game:GetService("RunService").Heartbeat:Wait() do
    if jh and jh:FindFirstChild("UpperTorso") then
        local vroot = jh:FindFirstChild("UpperTorso")
        local args = {
            [1] = "\243\160\128\160\243\160\128\131\243\160\128\157\243\160\128\143\243\160\128\188\243\160\128\168",
            [2] = {
                ["Limb"] = "UpperTorso",
                ["Character"] = jh,
                ["Point"] = Vector3.new(vroot.Position.X, vroot.Position.Y, vroot.Position.Z),
                ["Hit"] = vroot
            },
            [3] = false,
          
            [4] = player.Name .. "-12387781526-6193893072"
        }
        game:GetService("Players").LocalPlayer.Character.Core.Communicate:FindFirstChild(""):FireServer(unpack(args))
    end
end

Source: https://cheater.fun/hacks_roblox/9696-fight-in-a-school-roblox-auto-farm-scripts-and-hacks.html
title: Using the Script Editor
section: Extend:Scripting
project: /libs/scijava
artifact: org.scijava:script-editor
---

The script editor is an invaluable help when writing scripts in any of the [SciJava](/libs/scijava) framework's supported [languages](/scripting/comparisons).

## Features

Text Editing  

-   Full undo support
-   Auto-indent
-   Configurable white-space options

Programming  

-   Syntax highlighting
-   Output console
-   Git integration (file being edited must be part of a [Git](/develop/git) repository)
-   Language specific [templates](/scripting/templates)
-   Find and replace using regex patterns
-   Automatic brace highlighting
-   Line numbers

Language specific tools  

-   Organization of `import` declarations
-   Access to online documentation ([Javadocs](http://javadoc.scijava.org/), [ImageJ Macro Functions](https://imagej.net/ij/developer/macro/functions.html))
-   Access to source code in `.jar` files

Interface  

-   Bookmarks
-   Tabs for easy switching between open files
-   Navigation shortcuts

## Usage

### Starting the editor

To get started, start up the script editor:

<img src="/media/scripting/script-editor-new.jpg" width="500"/>

There is also the keyboard shortcut {% include key key='[' %} (open square bracket) to open the editor.

### Choosing a language

Then choose a language from the language menu:

![Script-Editor-choose-language.jpg](/media/scripting/script-editor-choose-language.jpg)

Now you can write your script. In this tutorial, Jython was chosen as scripting language, but the process is really the same for all scripting languages.

![](/media/script-editor-first-script.jpg)

### Running the script

Once you are satisfied with the script, run it. This does not require saving, but of course you should save your script later when it works.

![](/media/scripting/script-editor-run.jpg)

Note that while the script is running, the window title shows the tell-tale *(Running)*.

{% include warning/importing-classes %}

You can use all of ImageJ's classes right away. Here is an example that shows a dialog where the user can input a number. For details how to write dialogs in the different scripting languages, see [Scripting comparisons](/scripting/comparisons).

![](/media/scripting/script-editor-dialog.jpg)

## Further reading

See the [Scripting overview](/scripting) page for an introduction to scripting, and list of available languages, with links to more documentation.
