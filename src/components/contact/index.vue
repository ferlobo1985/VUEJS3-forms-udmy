<template>
  <form>
    <div class="row">
      <div class="col-xl-12">
        <h1>Contact us</h1>
        <hr />

        <div class="form-group">
          <label for="name">Name</label>
          <input
            type="text"
            id="name"
            class="form-control"
          />
        </div>

        <div class="form-group">
          <label for="email">email</label>
          <input
            type="email"
            id="email"
            class="form-control"
          />
        </div>

        <div class="form-group">
          <label for="subject">Subject</label>
          <input
            type="text"
            id="subject"
            class="form-control"
          />
        </div>

        <div class="form-group">
          <label for="message">Message</label>
          <textarea
            class="form-control"
            rows="3"
            id="message"
          ></textarea>
        </div>


        <div class="form-group">
            <h5>Want more spam ? </h5>
            <div class="form-check">
                <input class="form-check-input" type="checkbox" value="Newsletter" id="newsletter">
                <label class="form-check-label" for="newsletter">
                    Newsletter
                </label>
            </div>
            <div class="form-check">
                <input class="form-check-input" type="checkbox" value="Promotions" id="promotions">
                <label class="form-check-label" for="newsletter">
                    Promotions
                </label>
            </div>
         </div>

        <div class="form-group">
            <h5>What are you ? </h5>
            <div class="form-check">
                <input class="form-check-input" type="radio" id="human" value="human" name="origin">
                <label class="form-check-label" for="human">
                    Human
                </label>
            </div>
            <div class="form-check">
                <input class="form-check-input" type="radio" id="alien" value="alien" name="origin">
                <label class="form-check-label" for="alien">
                    Alien
                </label>
            </div>
        </div>

        <div class="form-group">
          <label for="country">Country</label>
          <select class="form-control" id="country">
            <option>
              Francisland
            </option>
          </select>
        </div>

       
      </div>
    </div>
  </form>
</template>
