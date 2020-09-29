Please download the files in [Pacman-fixes folder](Pacman-fixes) and overwrite them in your repo. No change is major. See details below.

# Capture.py

The main change in this file fixes the following error due to migrating the codebase to python3 from python2.

## Blue Agent coudn't find Capsules located in the middle of the screen:

Given a scenario like the one below, the blue team doesn't see the capsule at the last row.
```
%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%
%.%.%..%     ..%  % ..%..        %
%.%.% %% %%%%%%%     %%%%% %%%%% %
% % % .%  %. ..%    ... .        %
%.% % %%  %% %%%  . % %%%%%% %% %%
%   % .%  %    %      .   %. %  .%
%%% % %%   .%% %  %    .  %    % %
%.% %     %    %    %% %%    %   %
%.% %%%%%%% %%    %       %  % % %
% % %  %       %    %% %%%%%%% %.%
%   %    %% %%    %    %     % %.%
% %    %  .    %  % %%.   %% % %%%
%.  % .%   .      %    %  %. %   %
%% %% %%%%%% % .  %%% %%  %% % %.%
%        . ...    %.. .%  %. % % %
%  %%%%% %%%%%    %%%%%%% %% %.%.%
%        ..%.. % o%..     %..%.%.%
%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%
```
Lines Changed [capture.py#L350](Pacman-fixes/capture.py#L350), namely, the inequalities in both if statements: 

```python
def halfList(l, grid, red):
    halfway = grid.width // 2
    newList = []
    for x,y in l:
        if red and x < halfway: newList.append((x,y))
        elif not red and x >= halfway: newList.append((x,y))
    return newList
```

# CaptureAgents.py

This will not affect any behaviour, as we only change the comment/documentation:

```python
def getAction(self, gameState):
"""
Calls chooseAction on a grid position, but continues on half positions. 
If you subclass CaptureAgent, you shouldn't need to override this method.
It takes care of appending the current gameState on to your observation history 
(so you have a record of the game states of the game) and will call your choose 
action method if you're in a state (rather than halfway through your last 
move - this occurs because Pacman agents move half as quickly as ghost agents).
"""
```
This comment has been removed:

```
(rather than halfway through your last move - this occurs because Pacman agents 
move half as quickly as ghost agents).
```

Given that all agents move at the same speed.

# CaptureGraphics.py

Changes are only affecting the UI, where the status bar with the names now displays better names that are too long

# Replay.py

See [FAQ-Pacman.md](FAQ-Pacman.md#how-do-i-replay-a-game)