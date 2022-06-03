# CBlob@ class
Blob class is used for pretty much everything. Its one of the core parts of KAG. Anything from players characters, spawn points like tents, boats and much more are a blob.

---

## void Init()
This calls all current scripts attached to the blob ``onInit(CBlob@ this)`` hook.
<br>
Called automatically when using ``server_CreateBlob(const string&in, int team, Vec2f Position)``
<br>
Can be called manually after using ``server_CreateBlobNoInit(const string&in)``, so attributes can be set before onInit is called
<br>
<br>
<small>Returns: void</small>

<details>
<summary>Example</summary>

```as
CBlob@ new_blob = server_CreateBlobNoInit("new_blob"); // new blob
if (new_blob !is null)
{
    new_blob.Tag("very-cool-tag"); // set some important tag/info
    new_blob.Init(); // tell the blob to Init all scripts
}
```

</details>
<br>
<br>

## float getHealth()
This returns an f32 in the amount of HP the blob currently has.
<br>
<br>
<small>Returns: f32 - current health (amount of hearts / 2)</small>

<details>
<summary>Example</summary>

```as
f32 currentHp = this.getHealth(); // lets say we have 2 hearts
print(currentHp+''); // this would print '1.0'
```

</details>
<br>
<br>

## float getInitialHealth()
This returns an f32 with the amount of HP stated in our blobs .cfg file.
<br>
<br>
<small>Returns: f32 - with starting hp (hearts / 2)</small>

<details>
<summary>Example</summary>

```as
f32 hpOnStart = this.getInitialHealth(); // lets say we started off with 3 hearts
print(hpOnStart+''); // this would print '1.5'
```

</details>
<br>
<br>

## Vec2f getPosition()
This returns the most recent location of the blob in the world.
<br>
<br>
<small>Returns: Vec2f

<br>
<br>

## Vec2f getOldPosition()
This returns the position that was set previously before the blob's current position.
<br>
<br>
<small>Returns: Vec2f

<br>
<br>

## Vec2f getInterpolatedPosition()
This returns a 'smoothened' position that compensates for the difference between the blob's old and new position.
<br>
This is mainly used for GUI and other rendering since it is smoother.
<br>
<br>
<small>Returns: Vec2f

<br>
<br>

## void setPosition(Vec2f pos)
Set the blob's world position.
<br>
If this is done clientside for a player's blob it will be synced.  If this is done serverside for any other blob it will be synced.
<br>
<br>
<small>Returns: void

<details>
<summary>Example</summary>

```as
Vec2f mapCenter = getMap().getMapDimensions() / 2; // grab the dimensions of the map and then divide by 2 to find the map's center
this.setPosition(mapCenter); // this would teleport the blob from anywhere to the center of map
```

</details>
<br>
<br>

## Vec2f getVelocity()
This returns the velocity of the blob.
<br>
<br>
<small>Returns: Vec2f

<br>
<br>

## Vec2f getOldVelocity()
This returns the previous velocity that was set before the blob's current velocity.
<br>
<br>
<small>Returns: Vec2f

<br>
<br>

## void setVelocity(Vec2f vel)
Set the velocity of the blob.
<br>
<br>
<small>Returns: void

<details>
<summary>Example</summary>

```as
Vec2f velocity = this.getVelocity(); //our current velocity
this.setVelocity(velocity * 2); // double the blob's velocity (the blob would speed up 2x)
```

</details>

<br>
