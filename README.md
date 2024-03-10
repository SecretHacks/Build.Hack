# Roblox.Hack
its an test it maybe not working!!

the script:

local function highlightPlayer(player, highlight)
  local character = player.Character
  if character then
    local highlightObject = character:FindFirstChild("Highlight")
    if highlightObject then
      highlightObject.Enabled = highlight
    end
  end
end

game:GetService("UserInputService").InputBegan:Connect(function(input)
  if input.KeyCode == Enum.KeyCode.MouseHover then
    local ray = workspace.CurrentCamera:GetMouseRay(Vector2.new(input.Position.X, input.Position.Y))
    local targetPart = ray.Hit:FindFirstChildOfClass("Part")
    if targetPart then
      local highlightedPlayer = targetPart.Parent:FindFirstAncestor("Player")
      if highlightedPlayer then
        for _, player in pairs(game.Players:GetPlayers()) do
          highlightPlayer(player, player == highlightedPlayer) -- Highlight only the hovered player
        end
      end
    end
  end
end)
